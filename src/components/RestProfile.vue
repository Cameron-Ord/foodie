<template>
    <div>
        <main class="page_main">
            <section class="section_main">
                <article class="article_1">

                    <div class="article_1_div">

                        <h1>Welcome, {{ rest_data_holder[`name`] }}</h1>

                        <img v-bind:src="rest_data_holder[`profile_url`]">

                    </div>

                    <span class="span_1">

                        <p>Email: {{ rest_data_holder[`email`] }}</p>

                        <p>Address: {{ rest_data_holder[`address`] }}</p>

                        <p>Phone Number: {{ rest_data_holder[`phone_number`] }}</p>

                        <p>Bio: {{ rest_data_holder[`bio`] }}</p>

                        <p>Location: {{ rest_data_holder[`city`] }}</p>

                    </span>
                    <span class="span_2">

                        <h1>Edit your profile:</h1>

                        <p>Change business email:</p>

                        <input placeholder="enter a new email" type="text" ref="change_email">

                        <button @click="change_email">Change email</button>

                        <p>Change phone number:</p>

                        <input placeholder="enter a new phone number" type="text" ref="change_number">

                        <button @click="change_phone">Change phone number</button>

                        <p>Change address:</p>

                        <input placeholder="enter your new address" type="text" ref="change_address">

                        <button @click="change_address">Change address</button>

                        <p>Edit your bio:</p>

                        <input placeholder="write your information here" type="text" ref="change_bio">

                        <button @click="change_bio">Change bio</button>

                        <p>Change banner:</p>

                        <input placeholder="upload your image here" type="text" ref="change_banner">

                        <button @click="change_banner">Change banner</button>

                    </span>

                </article>

                <article class="article_2">

                    <menu-add></menu-add>

                </article>
                <article class="article_3">

                    <single-menu-item></single-menu-item>

                </article>
                <article class="incoming_orders">

                    <h1>Incoming Orders:</h1>

                    <div v-for="(order, i) in unconfirmed_orders" :key="i">

                        <div v-if="unconfirmed_orders[i][`is_confirmed`] != 1">

                            <h1>Order number: {{ order.order_id }} </h1>

                            <p>{{ order.name }}</p>



                        </div>

                        <button :clicked_confirm="i" @click="confirm_order" ref="confirmed_order">Confirm Orders</button>

                    </div>
                </article>
                <article class="confirmed_orders">

                    <h1>Confirmed Orders:</h1>

                    <span v-for="(confirmed, i) in confirmed_orders" :key="i">

                        <div v-if="(confirmed_orders[i][`is_confirmed`] != 0 && confirmed_orders[i][`is_completed`] != 1)">
                            <h1>Order number: {{ confirmed.order_id }}</h1>

                            <p>{{ confirmed.name }}</p>

                            <button :clicked_complete="i" @click="complete_order" ref="completed_order">Complete
                                Order</button>
                        </div>

                    </span>

                </article>


                <article class="completed_orders">

                    <h1>Completed Orders:</h1>

                    <span v-for="(completed, i) in completed_orders" :key="i">

                        <div v-if="(completed_orders[i][`is_completed`] != 0 && completed_orders[i][`is_confirmed`] != 0)">

                            <h1>Order number: {{ completed.order_id }} - {{ completed.name }}</h1>

                        

                        </div>


                    </span>


                </article>

                <article class="article_4">

                    <span class="span_1">

                        <h1>Account Settings:</h1>

                        <input placeholder="enter your password to delete your account" type="text" ref="delete_acc">


                        <button @click="delete_account">Delete Account</button>

                    </span>

                </article>
            </section>
        </main>

    </div>
</template>

<script>

import axios from 'axios';
import Cookies from 'vue-cookies';
import SingleMenuItem from './SingleMenuItem.vue';
import MenuAdd from './MenuAdd.vue';
export default {


    components:{

        SingleMenuItem,
        MenuAdd


    },

    data() {
        return {

            index: 0,

            rest_data_holder: {},

            unconfirmed_orders: [],

            confirmed_orders: [],

            completed_orders: [],


        }
    },

    methods: {

        confirm_order(details) {

            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`confirmed_order`] = details.currentTarget;

            let button_clicker = this.$refs[`confirmed_order`].getAttribute(`clicked_confirm`);

            let confirmed_item = this.unconfirmed_orders[button_clicker][`order_id`];


            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant-order`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    order_id: confirmed_item,

                    is_confirmed: "true",


                },

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            })

        },

        complete_order(details) {

            let restaurant_token = Cookies.get(`rest_login_token`);

            this.$refs[`completed_order`] = details.currentTarget;

            let button_clicker = this.$refs[`completed_order`].getAttribute(`clicked_complete`);

            let completed_item = this.confirmed_orders[button_clicker][`order_id`];



            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant-order`,

                headers: {
                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    order_id: completed_item,

                    is_complete: "true",


                },


            }).then((response) => {

                response;


            }).catch((error) => {
                error;


            });




        },


        delete_account() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `DELETE`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {


                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    password: this.$refs[`delete_acc`][`value`],

                }

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });


        },


        change_email() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    email: this.$refs[`change_email`][`value`],
                }

            }).then((response) => {

                response;


            }).catch((error) => {

                error;

            });

        },

        change_phone() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    phone_number: this.$refs[`change_number`][`value`],
                }

            }).then((response) => {

                response;


            }).catch((error) => {

                error;

            });

        },

        change_address() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    address: this.$refs[`change_address`][`value`],
                }

            }).then((response) => {

                response;


            }).catch((error) => {

                error;

            });

        },

        change_bio() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    bio: this.$refs[`change_bio`][`value`],
                }

            }).then((response) => {

                response;


            }).catch((error) => {

                error;

            });


        },

        change_banner() {

            let restaurant_token = Cookies.get(`rest_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/restaurant`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: restaurant_token,
                },

                data: {

                    banner_url: this.$refs[`change_banner`][`value`],
                }

            }).then((response) => {

                response;


            }).catch((error) => {

                error;

            });



        },


    },




    mounted() {


        let rest_id_value = Cookies.get(`restaurant_id`);


        axios({


            method: `GET`,


            url: `https://foodie.bymoen.codes/api/restaurant`,


            headers: {


                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`


            },


            params: {


                restaurant_id: rest_id_value,
            }




        }).then((response) => {

            response;




            this.rest_data_holder = response[`data`][0];



        }).catch((error) => {


            error

        });


        let rest_token = Cookies.get(`rest_login_token`);

        axios({

            method: `GET`,

            url: `https://foodie.bymoen.codes/api/restaurant-order`,

            headers: {

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: rest_token,


            },

            params: {

                is_confirmed: "false",

                is_complete: "false"
            }

        }).then((response) => {

            response;

            for (let i = 0; i < response[`data`].length; i++) {

                this.unconfirmed_orders.push(response[`data`][i]);

            }



        }).catch((error) => {

            error;

        });


        axios({

            method: `GET`,

            url: `https://foodie.bymoen.codes/api/restaurant-order`,

            headers: {

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: rest_token,


            },

            params: {

                is_confirmed: "true",

                is_complete: "false"


            }

        }).then((response) => {

            response;


            for (let i = 0; i < response[`data`].length; i++) {

                this.confirmed_orders.push(response[`data`][i]);

            }



        }).catch((error) => {

            error;

        });

        axios({

            method: `GET`,

            url: `https://foodie.bymoen.codes/api/restaurant-order`,

            headers: {

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: rest_token,


            },

            params: {


                is_complete: "true",


            }

        }).then((response) => {

            response;

            for (let i = 0; i < response[`data`].length; i++) {

                this.completed_orders.push(response[`data`][i]);




            }


        }).catch((error) => {

            error;

        });




    }





}
</script>

<style scoped>

.page_main{

    display: grid;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    justify-items: center;

    align-items: center;


}


.section_main{

    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 1fr 0.4fr 0.6fr 0.2fr 0.2fr 0.2fr 0.6fr;


}

.article_1 {
    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;
}

.article_1>.article_1_div {

    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 10vh 1fr;

    width: 100%;
}

.article_1>.article_1_div>img {

    width: 100%;

    object-fit: cover;

}

.article_1>.span_1 {

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 7vh 7vh 7vh 1fr 7vh;

    width: 100%;

}

.article_1>.span_2 {

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;

}

.article_2 {


    display: grid;

    justify-items: center;

    align-items: center;
}

.article_2>.span_1 {


    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;

}
.article_3 {
    display: grid;

    justify-items: center;

    align-items: center;

    grid-auto-flow: row;
}

.article_3>.span_1 {

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 10vh 35vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;


}

.article_3>.span_1>img {

    width: 125px;
    height: 125px;

}


.article_4 {
    display: grid;
    justify-items: center;

    align-items: center;

    text-align: center;
}

.article_4>.span_1 {


    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh;
}

.incoming_orders{

    display: grid;

    align-items: center;

    justify-items: center;

    grid-auto-flow: row;
}

.confirmed_orders{
    display: grid;

    align-items: center;

    justify-items: center;

    grid-auto-flow: row;

}

.completed_orders{
    display: grid;

    align-items: center;

    justify-items: center;

    grid-auto-flow: row;


}

.incoming_orders>span{

    display: grid;

    align-items: center;

    justify-items: center;

    grid-auto-flow: row;

}

.incoming_orders>span>div{

display: grid;

align-items: center;

justify-items: center;


}

.confirmed_orders>span{

display: grid;

align-items: center;

justify-items: center;

grid-auto-flow: row;

}

.confirmed_orders>span>div{

display: grid;

align-items: center;

justify-items: center;


}

.completed_orders>span{

display: grid;

align-items: center;

justify-items: center;

grid-auto-flow: row;

}

.completed_orders>span>div{

display: grid;

align-items: center;

justify-items: center;

margin-top: 5px;

margin-bottom: 5px;

}


</style>