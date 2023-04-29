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

                    headers:{


                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                    },

                    data:{

                        email: this.$refs[`email_input`].value,
                        password: this.$refs[`password_input`].value

                    }
                }).then((response)=>{

                    console.log(response);

                    Cookies.set(`rest_login_token`, `${response[`data`][`token`]}`);

                    Cookies.set(`restaurant_id`, `${response[`data`][`restaurantId`]}`);

                    Cookies.remove(`client_login_token`);

                    Cookies.remove(`client_id_token`);

                    this.$router.push(`/`);

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