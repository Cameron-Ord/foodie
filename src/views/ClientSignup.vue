<template>
    <div>

        <page-header></page-header>

        <main class="page_main">

            <section class="section_main">

                <article class="input_article">

                    <span class="input_span">

                        <input placeholder="your email" type="value" ref="email_input">
                        <input placeholder="your name" type="value" ref="name_input">
                        <input placeholder="your last name" type="value" ref="last_name_input">
                        <input placeholder="your avatar" type="value" ref="avatar_input">
                        <input placeholder="username" type="value" ref="username_input">
                        <input placeholder="password" type="value" ref="password_input">

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
import Cookies from 'vue-cookies';



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


            axios({

                method: `POST`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                },

                data: {


                    email: this.$refs[`email_input`].value,

                    first_name: this.$refs[`name_input`].value,

                    last_name: this.$refs[`last_name_input`].value,

                    image_url: this.$refs[`avatar_input`].value,

                    username: this.$refs[`username_input`].value,

                    password: this.$refs[`password_input`].value


                }



            }).then((response) => {

                console.log(response);

                Cookies.set(`client_login_token`, `${response[`data`][`token`]}`);

                Cookies.set(`client_id_token`, `${response[`data`][`client_id`]}`);


                Cookies.remove(`rest_login_token`);

                Cookies.remove(`restaurant_id`);

            }).catch((error) => {

                console.log(error);

            });

        }

    }

}
</script>

<style scoped>
.page_main {

    display: grid;

    align-items: center;

    justify-items: center;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

}


.page_main>.section_main {

    display: grid;

    align-items: center;

    width: 100%;
}

.page_main>.section_main>.input_article {

    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 1fr 1fr;

    width: 100%;
}

.page_main>.section_main>.input_article>.input_span {

    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 25px 25px 25px 25px 25px 25px;

    width: 85%;
}

.page_main>.section_main>.input_article>.tinyspan {

    display: grid;

    align-items: center;

    grid-template-rows: 50px 50px;

    width: 85%;
}
</style>