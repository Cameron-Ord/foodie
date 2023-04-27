<template>
    <div>
        <main>
            <section>
                <article>
                    <span>

                        <h1>Welcome, {{ client_data_holder[`username`] }}</h1>

                    </span>
                    <span>

                        <h1>Account info:</h1>

                        <img v-bind:src="client_data_holder[`image_url`]">

                        <p>Email: {{ client_data_holder[`email`] }}</p>

                        <p>First-name: {{ client_data_holder[`first_name`] }}</p>

                        <p>last-name: {{ client_data_holder[`last_name`] }}</p>

                        <p>username: {{ client_data_holder[`username`] }}</p>

                    </span>

                    <span>

                        <h1>Edit your profile:</h1>

                        <p>Change username:</p>

                        <input placeholder="enter a new username" type="text">

                        <p>Change avatar:</p>

                        <input placeholder="upload an image" type="text">

                        <p>Change password:</p>

                        <input placeholder="enter a password" type="password">
                    </span>

                    <span>

                        <h1>Account settings:</h1>

                        <button @click="delete_profile">Delete Account</button>


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

            client_data_holder: {}
        }
    },



    methods: {

        delete_profile(){

            
        }

    },

    mounted() {


 

        let client_token = Cookies.get(`client_login_token`);

        let client_id_value = Cookies.get(`client_id_token`);

        if (client_token !== undefined) {

            axios({

                method: `GET`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                },

                params: {

                    client_id: client_id_value,

                }


            }).then((response) => {

                response;
                console.log(`client profile api success`);

                this.client_data_holder = response[`data`][0];

            }).catch((error) => {

                error;

            });

        }

    }
}
</script>

<style scoped>

</style>