<template>
    <div>
        <main>
            <section>
                <article>
                    <span>

                        <h1>Welcome, {{ client_data_holder[`username`] }}</h1>

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