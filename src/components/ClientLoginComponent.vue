<template>
    <span class="Client_Comp">

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

        
                    headers:{


                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                    },

                    data:{

                        email: this.$refs[`email_input`].value,
                        password: this.$refs[`password_input`].value

                    }

                }).then((response)=>{

                    response;

                    Cookies.set(`client_login_token`, `${response[`data`][`token`]}`);

                    Cookies.set(`client_id_token`, `${response[`data`][`client_id`]}`);

                    Cookies.remove(`rest_login_token`);

                    Cookies.remove(`restaurant_id`);

                    this.$router.push(`/`);



                }).catch((error)=>{

                    error;

                });
            }
        },

    }
</script>

<style scoped>
.Client_Comp{

display: grid;

justify-items: center;

align-items: center;

grid-template-rows: 50px 50px;

}
</style>