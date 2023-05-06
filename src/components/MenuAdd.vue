<template>
                    <span class="span_1">

                        <h1>Add, modify, or remove your menu items:</h1>

                        <p>Name</p>
                        <input type="text" ref="Name_Box_Add">
                        <p>Description</p>
                        <input type="text" ref="Desc_Box_Add">
                        <p>Image</p>
                        <input type="text" ref="Image_Box_Add">
                        <p>Price</p>
                        <input type="text" ref="Price_Box_Add">

                        <button @click="add_product">Add</button>


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


              add_product() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            let rest_id_value = Cookies.get(`restaurant_id`);

            console.log(this.$refs[`Name_Box_Add`][`value`]);

            if (rest_id_value !== undefined) {

                axios({

                    method: `POST`,

                    url: `https://foodie.bymoen.codes/api/menu`,

                    headers: {

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                        token: restaurant_token

                    },

                    data: {


                        name: this.$refs[`Name_Box_Add`][`value`],
                        description: this.$refs[`Desc_Box_Add`][`value`],
                        image_url: this.$refs[`Image_Box_Add`][`value`],
                        price: this.$refs[`Price_Box_Add`][`value`]

                    },


                }).then((response) => {


                    response;

                  

                }).catch((error) => {

                    error;

                });

            }



        },

        }
    }
</script>

<style scoped>

</style>