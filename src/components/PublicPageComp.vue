<template>
    <span>

        <h1>{{ restaurant_object[`name`] }}</h1>

      <img :src="restaurant_object[`banner_url`]">

      <p>{{ restaurant_object[`city`] }}</p>

      <p>{{ restaurant_object[`address`] }}</p>
    
      <p>{{ restaurant_object[`phone_number`] }}</p>

      <p>{{ restaurant_object[`bio`] }}</p>





    </span>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {
        

        data() {
            return {
               restaurant_object: {}
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


          


        }
    }
</script>

<style scoped>

</style>