<template>
    <div>

        <main class="page_main">

            <section class="section_main">

                <article class="article_main">

    
                    <span class="Client_Comp">

                        <h1>Email:</h1>
    
                        <input placeholder="..." type="text" ref="email_input">
    
                        <h1>Password:</h1>

                        <input placeholder="..." type="password" ref="password_input">
    
                        <button @click="user_log_in" ><h1>Log In</h1></button>
    
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

.page_main{

    display: grid;

    justify-items: center;

    align-items: center;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    width: 100%;

    color: #FFFFFF;

}

.page_main>.section_main{

    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;

}

.page_main>.section_main>.article_main{

    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;


}
.page_main>.section_main>.article_main>.Client_Comp{

display: grid;

justify-items: center;

align-items: center;

grid-template-rows: 75px 50px 75px 50px 100px;

background-color: #003F91;

width: 80%;

border-radius: 25px;
}

.page_main>.section_main>.article_main>.Client_Comp>input{


    width: 50vw;

}

.page_main>.section_main>.article_main>.Client_Comp>button{


    color: #FFFFFF;

    background-color: #003F91;

    padding: 10px;

}
</style>