<template>
    <span>

        <input type="text" ref="email_input">
        <input type="password" ref="password_input">
        <button @click="user_log_in" >log in</button>

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

            user_log_in(){

                axios({

                    method: `POST`,

                    url: `https://foodie.bymoen.codes/api/client-login`,

                    data:{

                        email: this.$refs[`email_input`].values,
                        password: this.$refs[`password_input`].value

                    }

                }).then((response)=>{

                    response;

                    Cookies.set(`client_login_token`, `${response[`data`][`token`]}`);

                    Cookies.set(`client_id_token`, `${response[`data`][`client_id`]}`);

                }).catch((error)=>{

                    error;

                });
            }
        },

    }
</script>

<style scoped>

</style>