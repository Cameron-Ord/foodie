<template>
    <div>
           

        <page-header></page-header>

        <main class="page_main">

            <section class="section_main">

                <article class="input_article">

                    <span class="input_span">

                        <input placeholder="your email"  type="text" ref="email_input">
                        <input placeholder="your name" type="text" ref="name_input">
                        <input placeholder="address" type="text" ref="address_input">
                        <input placeholder="phone number" type="text" ref="phone_input">
                        <input placeholder="bio"  type="text" ref="bio_input">
                        <input placeholder="city"  type="text" ref="city_input">
                        <input placeholder="profile image" type="text" ref="profile_input">
                        <input placeholder="banner image" type="text" ref="banner_input">
                        
                        <input placeholder="password" type="password" ref="password_input">

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

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                },
                
                method: `POST`,

                data: {


                    email: this.$refs[`email_input`].value,
                    name: this.$refs[`name_input`].value,
                    address: this.$refs[`address_input`].value,
                    phone_number: this.$refs[`phone_input`].value,
                    bio: this.$refs[`bio_input`].value,
                    city: this.$refs[`city_input`].value,
                    profile_url: this.$refs[`profile_input`].value,
                    banner_url: this.$refs[`banner_input`].value,
                    password: this.$refs[`password_input`].value,


                }



            }).then((response) => {

                response;

                Cookies.set(`token`, `${response[`data`][`token`]}`);

                Cookies.set(`id`, `${response[`data`][`restaurant_id`]}`)


            }).catch((error) => {

                error;

                console.log(`api failure`);

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

    grid-template-rows: 25px 25px 25px 25px 25px 25px 25px 25px 25px;

    width: 85%;
}

.page_main>.section_main>.input_article>.tinyspan{

        display: grid;

    align-items: center;

    grid-template-rows: 50px 50px;

    width: 85%;


}
</style>