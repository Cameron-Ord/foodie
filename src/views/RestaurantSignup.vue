<template>
    <div>
           

        <page-header></page-header>
        <main>

            <section>
                <article>

                    <restaurant-login-component></restaurant-login-component>
                    

                </article>
                <article>

                    <span>

                        <input placeholder="your email"  type="text" ref="email_input">
                        <input placeholder="your name" type="text" ref="name_input">
                        <input placeholder="address" type="text" ref="address_input">
                        <input placeholder="phone number" type="text" ref="phone_input">
                        <input placeholder="bio"  type="text" ref="bio_input">
                        <input placeholder="city"  type="text" ref="city_input">
                        <input placeholder="profile image" type="text" ref="profile_input">
                        <input placeholder="banner image" type="text" ref="banner_input">
                        
                        <input placeholder="password" type="password" ref="password_input">

                        <button @click="sign_up">Create Account</button>
                        

                        <h4>Already have an account? Log in</h4>


                    </span>
                </article>
            </section>

        </main>

    </div>
</template>

<script>

import RestaurantLoginComponent from '@/components/RestaurantLoginComponent.vue';
import PageHeader from '@/components/PageHeader.vue';
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {

            components: {

                RestaurantLoginComponent,

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

</style>