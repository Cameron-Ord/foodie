<template>
    <span class="Rest_Comp">

        <input type="text" ref="email_input">
        <input type="password" ref="password_input">
        <button @click="rest_log_in" >log in</button>

    </span>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {
        
        data() {
            return {
                
            }
        },

        methods:{

            rest_log_in(){


                axios({

                    method: `POST`,

                    url: `https://foodie.bymoen.codes/api/restaurant-login`,

                    data:{

                        email: this.$refs[`email_input`].values,
                        password: this.$refs[`password_input`].values

                    }
                }).then((response)=>{

                    response;

                    Cookies.set(`rest_login_token`, `${response[`data`][`token`]}`);

                    Cookies.set(`restaurant_id`, `${response[`data`][`restaurant_id`]}`);

                }).catch((error)=>{

                    error;

                });

            }
        }
    }
</script>

<style scoped>

.Rest_Comp{

    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 50px 50px;

}

</style>