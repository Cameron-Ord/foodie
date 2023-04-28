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

                    </span>
                </article>
            </section>
        </main>

    </div>
</template>

<script>
import axios from 'axios';

    export default {


        data() {
            return {
               restaurants: [],
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

                    this.restaurants.push(response[`data`][i])

       
                }


                console.log(this.restaurants);
            }).catch((error) =>{

                error;

            })
        
       
        
        }

    }
</script>

<style scoped>

</style>