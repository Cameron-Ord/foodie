<template>
    <div>
 
        <page-header></page-header>

        <main class="page_main">

            <section class="section_main">

                <article class="input_article">

                    <span class="input_span">

                        <input placeholder="your email" class="email" type="value">
                        <input placeholder="your name" class="name" type="value">
                        <input placeholder="your last name" class="last_name" type="value">
                        <input placeholder="your avatar" class="user_avatar" type="value">
                        <input placeholder="username" class="username" type="value">
                        <input placeholder="password" class="password" type="value">

                    </span>
                    <span class="tinyspan">

                        <button @click="sign_up">Create Account</button>
                        

                        <h4>Already have an account? Log in</h4>
                    </span>
                </article>
            </section>

        </main>

    </div>
</template>

<script>

import PageHeader from '@/components/PageHeader.vue';
import axios from 'axios';



export default {
    components: {
 


        PageHeader,

    },



    data() {
        return {

        }
    },



    methods: {


        sign_up() {

            let email_input = document.querySelector(`.email`);

            let email_input_value = email_input[`value`];

            let name_input = document.querySelector(`.name`);

            let first_name_value = name_input[`value`];

            let last_name = document.querySelector(`.last_name`);

            let last_name_value = last_name[`value`];

            let avatar_input = document.querySelector(`.user_avatar`);

            let image_url_value = avatar_input[`value`];

            let username_input = document.querySelector(`.username`);

            let username_value = username_input[`value`];

            let password_input = document.querySelector(`.password`);

            let password_value = password_input[`value`];

            axios({

                method: `POST`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                },

                data: {


                    email: email_input_value,

                    first_name: first_name_value,

                    last_name: last_name_value,

                    image_url: image_url_value,

                    username: username_value,

                    password: password_value


                }



            }).then((response) => {

                console.log(response);



            }).catch((error) => {

                console.log(error);

            });

        }

    }

}
</script>

<style scoped>

.page_main{

    display: grid;

    align-items: center;

    justify-items: center;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

}


.page_main>.section_main{

    display: grid;

    align-items: center;

    width: 100%;
}

.page_main>.section_main>.input_article{

    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 1fr 1fr;

    width: 100%;
}

.page_main>.section_main>.input_article>.input_span{
    
    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 25px 25px 25px 25px 25px 25px;

    width: 85%;
}
.page_main>.section_main>.input_article>.tinyspan{

    display: grid;

    align-items: center;

    grid-template-rows: 50px 50px;

    width: 85%;
}


</style>