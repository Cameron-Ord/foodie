<template>
    <div>
        <main>
            <section>
                <article>
              
                    <span>
                        <h1>Welcome, {{ rest_data_holder[`username`] }}</h1>
                    </span>
                    <span></span>
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
                

            rest_data_holder: {},
           
        }
        },


        mounted(){


        let restaurant_token = Cookies.get(`rest_login_token`);

        let rest_id_value = Cookies.get(`rest_login_token`);


            if (restaurant_token !== undefined) {

            axios({

                method: `GET`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                },

                params: {

                    restaurant_id: rest_id_value,
                }


            }).then((response) => {
                response;
                console.log(`restaurant profile api success`);

    
                this.rest_data_holder = response[`data`][0];


            }).catch((error) => {

                error
            });

        }
        }
    }
</script>

<style scoped>

</style>