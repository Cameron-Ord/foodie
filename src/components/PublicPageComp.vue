<template>
    <div>
    <article>
    <span>

        <h1>{{ restaurant_object[`name`] }}</h1>

      <img :src="restaurant_object[`banner_url`]">

      <p>{{ restaurant_object[`city`] }}</p>

      <p>{{ restaurant_object[`address`] }}</p>
    
      <p>{{ restaurant_object[`phone_number`] }}</p>

      <p>{{ restaurant_object[`bio`] }}</p>


    </span>
</article>
<article>

    <span v-for="(menu_item, i) in rest_menu" :key="i">

        <h1>{{ menu_item[`name`] }}</h1>

        <img :src="menu_item[`image_url`]">

        <p>{{ menu_item[`price`] }}</p>

    </span>

</article>
</div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {
        

        data() {
            return {
               restaurant_object: {},

               rest_menu: []
            }
        },


        mounted(){


            let chosen_restaurant_id = Cookies.get(`restaurant_selected`);

            if(chosen_restaurant_id !== undefined){

                axios({

                    method: `GET`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                    },

                    params:{

                        restaurant_id: chosen_restaurant_id

                    }


                }).then((response)=>{

 
                    this.restaurant_object = response[`data`][0];

                    console.log(this.restaurant_object);

                }).catch((error)=>{

                    error;

                    console.log(`API failure`);
                });


            }

            if(chosen_restaurant_id !== undefined){

            axios({

                method: `GET`,

                url: `https://foodie.bymoen.codes/api/menu`,

                
                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                    },

                    params:{

                        restaurant_id: chosen_restaurant_id

                    }


            }).then((response)=>{

                console.log(response)

                for (let i = 0; i < response[`data`].length; i++){

                    this.rest_menu.push(response[`data`][i]);
                }

                console.log(this.rest_menu);

            }).catch((error)=>{

                error

            })
        }


        }
    }
</script>

<style scoped>

</style>