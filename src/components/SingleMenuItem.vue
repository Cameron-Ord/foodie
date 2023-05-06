<template>
        <span class="span_1" v-if="j !== undefined">

                <h2>{{ menu_get_holder[j][`name`] }}</h2>
                
                <img :src="menu_get_holder[j][`image_url`]">

                <button @click="prev">Previous</button>

                <button @click="next">Next</button>



                <p>Change Name - {{ menu_get_holder[j][`name`] }}</p>

                <input type="value" class="name_type">

                <button :clicked_item="j" ref="product_clicked" @click="edit_name">Edit</button>

                <p>Change Description - {{ menu_get_holder[j].description }}</p>

                <input type="value" class="desc_type">

                <button :clicked_item="j" ref="product_clicked" @click="edit_desc">Edit</button>

                <p>Change Image</p>

                <input type="value" class="image_type">

                <button :clicked_item="j" ref="product_clicked" @click="edit_image">Edit</button>

                <p>Change Price - {{ menu_get_holder[j].price }} </p>

                <input type="value" class="price_type">

                <button :clicked_item="j" ref="product_clicked" @click="edit_price">Edit</button>

                <button :clicked_item="j" ref="product_clicked" @click="delete_product">Delete</button>

            </span>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
export default {
    data() {
        return {


            j: undefined,

            menu_get_holder: [],


        }
    },



    methods: {

        next() {

            this.j++;



            if (this.j > this.menu_get_holder.length - 1) {

                this.j = 0;

            }

        },


        prev() {

            this.j--;

            if (this.j < 0) {

                this.j = this.menu_get_holder.length - 1;
            }

        },

        delete_product(details) {


            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`product_clicked`] = details.currentTarget;

            let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

            let image = this.menu_get_holder[button_clicked][`id`];



            axios({

                method: `DELETE`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token

                },

                data: {

                    menu_id: image,
                }


            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });
        },


        edit_name(details) {

            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`product_clicked`] = details.currentTarget;

            let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

            let image = this.menu_get_holder[button_clicked][`id`];

            let name_input = document.querySelector(`.name_type`);

            let name_input_value = name_input[`value`];



            console.log(name_input_value);
            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token

                },

                data: {

                    menu_id: image,

                    name: name_input_value,



                }


            }).then((response) => {

                response;

                console.log(response);


            }).catch((error) => {

                error;


            })

        },

        edit_desc(details) {

            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`product_clicked`] = details.currentTarget;

            let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

            let image = this.menu_get_holder[button_clicked][`id`];

            let desc_input = document.querySelector(`.desc_type`);

            let desc_input_value = desc_input[`value`];




            console.log(desc_input_value);
            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token

                },

                data: {

                    menu_id: image,
                    description: desc_input_value


                }


            }).then((response) => {

                response;

                console.log(response);


            }).catch((error) => {

                error;


            })

        },

        edit_image(details) {
            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`product_clicked`] = details.currentTarget;

            let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

            let image = this.menu_get_holder[button_clicked][`id`];

            let image_input = document.querySelector(`.image_type`);

            let image_input_value = image_input[`value`];



            console.log(image_input_value);
            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token

                },

                data: {

                    menu_id: image,
                    image_url: image_input_value,



                }


            }).then((response) => {

                response;

                console.log(response);


            }).catch((error) => {

                error;


            })


        },

        edit_price(details) {

            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`product_clicked`] = details.currentTarget;

            let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

            let image = this.menu_get_holder[button_clicked][`id`];

            let price_input = document.querySelector(`.price_type`);

            let price_input_value = price_input[`value`];


            console.log(price_input_value);
            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token

                },

                data: {

                    menu_id: image,
                    price: price_input_value,



                }


            }).then((response) => {

                response;

                console.log(response);


            }).catch((error) => {

                error;


            })

        },

   },
   


        mounted(){


            console.log(this.j);
            let rest_id_value = Cookies.get(`restaurant_id`);

            axios({

                method: `GET`,

                url: `https://foodie.bymoen.codes/api/menu`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                },

                params: {

                    restaurant_id: rest_id_value,

                },
            }).then((response) => {

                response;

                for (let i = 0; i < response[`data`].length; i = i + 1) {

                    this.menu_get_holder.push(response[`data`][i]);

                  


                }

                this.j = 0;


            }).catch((error) => {

                error;

            });

            console.log(this.menu_get_holder);

        }
    }
</script>

<style scoped>





</style>