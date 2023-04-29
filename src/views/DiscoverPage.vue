<template>
    <div>
        <main>
            <section>
                <article v-for="(restaurant, i) in restaurants" :key="i">
                    <span>

                        <h1>{{ restaurant[`name`] }}</h1>

                        <p> {{ restaurant[`phone_number`] }}</p>

                        <p>{{ restaurant[`address`] }}</p>

                        <p>{{ restaurant[`bio`] }}</p>


                        <button :clicked_rest="i" @click="rest_chose" ref="button_clicked">view menu</button>

                    </span>
                </article>
            </section>
        </main>

    </div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
     export default {


        data() {
            return {
               restaurants: [],
            }
        },

        methods:{

            rest_chose(details){


                this.$refs[`button_clicked`] = details.currentTarget;
              
                let button_clicker = this.$refs[`button_clicked`].getAttribute(`clicked_rest`);

                let restaurant = this.restaurants[button_clicker];

                Cookies.set(`restaurant_selected`, restaurant[`restaurant_id`]);

                this.$router.push(`/PublicPage`);

            }
        },

        mounted(){

            axios({

                method: `GET`,

                url:`https://foodie.bymoen.codes/api/restaurants`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`
                },

            }).then((response)=>{

                response;

                for(let i = 0; i < response[`data`].length; i = i +1){

                    

                    this.restaurants.push(response[`data`][i]);

       
                }


            }).catch((error) =>{

                error;

            })
        
       
        
        }

    }
</script>

<style scoped>

</style>