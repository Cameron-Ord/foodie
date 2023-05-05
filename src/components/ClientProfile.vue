<template>
    <div>
        <main class="page_main">
            <section class="section_main">
                <article class="article_1">
                    <span class="article_1_span_2">

                        <h1>Welcome, {{ client_data_holder[`username`] }}</h1>

                        <h1>Account info:</h1>

                        <img v-bind:src="client_data_holder[`image_url`]">
                        </span>
                        <span class="article_1_span_1"> 

                        <p class="p_prof">Email:</p>
                        <p class="p_data">{{ client_data_holder[`email`] }}</p>

                        <p class="p_prof">First-name: </p>
                        <p class="p_data"> {{ client_data_holder[`first_name`] }}</p>

                        <p class="p_prof">last-name: </p>
                        <p class="p_data">{{ client_data_holder[`last_name`] }}</p>

                        <p class="p_prof">username: </p>
                        <p class="p_data">{{ client_data_holder[`username`] }}</p>

                    </span>

                    <span class="article_1_span_3">

                        <h1>Edit your profile:</h1>

                        <p>Change email:</p>

                        <input placeholder="enter a new email" type="text" ref="email_change">

                        <button @click="change_email">Update Email</button>

                        <p>Change username:</p>

                        <input placeholder="enter a new username" type="text" ref="username_change">

                        <button @click="change_username">Update Username</button>

                        <p>Change avatar:</p>

                        <input placeholder="upload an image" type="text" ref="avatar_change">

                        <button @click="change_avatar">Update Avatar</button>

                        <p>Change password:</p>

                        <input placeholder="enter a password" type="password" ref="password_change">

                        <button @click="change_password">Update Password</button>
                    </span>

                </article>

                <article class="orders">


                <span class="header_tag">
                    <h1>Current Orders:</h1>
                </span>
                    <div class="incomp_order" v-for="(item, i) in incomplete_orders" :key="i">
                    
                    
                        <span v-if="item.is_complete !== 1">

                            <h1>{{ item.name }} - {{ item.order_id }}</h1>

                        </span>
                    
                    
                    </div>
                 

                </article>

                <article class="completed_orders">

                <span class="header_tag">
                    <h1>Order History:</h1>

                </span>

                    <div class="comp_order" v-for="(item, i) in completed_orders" :key="i">
                    
                        <span v-if="item.is_complete !== 0">
                        
                        
                            <h1>{{ item.name }} - {{ item.order_id }}</h1>


                        </span>
                    
                    </div>



                </article>

                <article class="account_setting">
                    <span class="del_span">

                        <h1>Account settings:</h1>

                        <input placeholder="enter your password to delete your account" type="password"
                            ref="delete_account">

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

            client_data_holder: {},

            incomplete_orders: [],

            completed_orders: [],

            id_array: []
        }
    },



    methods: {

        delete_profile() {

            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `DELETE`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data: {

                    password: this.$refs[`delete_account`].value,
                }

            }).then((response) => {

                response;

                this.$router.push(`/`);
            }).catch((error) => {

                error;
            })


        },


        change_email() {

            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data: {

                    email: this.$refs[`email_change`].value,
                }

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });

        },

        change_username() {
            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data: {

                    username: this.$refs[`username_change`].value,
                }

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });

        },

        change_avatar() {

            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data: {

                    image_url: this.$refs[`avatar_change`].value,
                }

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });

        },

        change_password() {


            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers: {

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data: {

                    password: this.$refs[`password_change`].value,
                }

            }).then((response) => {

                response;

            }).catch((error) => {

                error;

            });

        },



        grouping(){

        

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
                this.client_data_holder = response[`data`][0];

            }).catch((error) => {

                error;

            });

        }


        axios({

            method: `GET`,

            url: `https://foodie.bymoen.codes/api/client-order`,

            headers: {

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: client_token

            },

            params: {

                is_complete: `false`
            }


        }).then((response) => {

        response;

            
            for (let i = 0; i < response[`data`].length; i++) {

                this.incomplete_orders.push(response[`data`][i]);
                
                Cookies.set(`orders`, this.incomplete_orders);

    

            }

            this.grouping();
        }).catch((error) => {

            error;

        });

        axios({

            method: `GET`,

            url: `https://foodie.bymoen.codes/api/client-order`,

            headers: {

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: client_token

            },

            params: {

                is_complete: "true"
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
.page_main {

    display: grid;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    align-items: center;

    justify-items: center;
}

.page_main>.section_main {

    display: grid;

    grid-auto-flow: row;

    align-items: center;

    justify-items: center;

    width: 100%;

}

.page_main>.section_main>.article_1 {

    display: grid;

    grid-auto-flow: row;

    align-items: center;

    justify-items: center;

    width: 100%;

    text-align: center;

}


.page_main>.section_main>.article_1>.article_1_span_1{


    display: grid;

    grid-auto-flow: row;

    justify-items: center;
    
    align-items: center;

    background-color: #003F91;
    
    width: 90%;

    margin-top: 25px;

    grid-template-rows: 10vh 5vh 10vh 5vh 10vh 5vh 10vh 5vh;

}


.page_main>.section_main>.article_1>.article_1_span_2 {

    display: grid;

    grid-template-rows: auto;

    align-items: center;

    justify-items: center;

    grid-template-rows: 15vh 5vh 30vh;

    background-color: #003F91;

    margin-top: 25px;

    width: 90%;

    text-align: center;

    color: #FFFFFF;

}


.page_main>.section_main>.article_1>.article_1_span_2>img {

    height: 125px;

    width: 125px;

    border-radius: 50%;

    border-style: solid;

    color: #5DA9E9;

    border-width: 10px;

}

.page_main>.section_main>.article_1>.article_1_span_3 {

    display: grid;

    grid-template-rows: auto;

    align-items: center;

    justify-items: center;

    grid-template-rows: 10vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;

    background-color: #003F91;

    margin-top: 25px;

    width: 90%;

    color: #FFFFFF;

    padding-top: 10px;

    padding-bottom: 10px;
}


.page_main>.section_main>.account_setting>.del_span {

    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 10vh 5vh 5vh;
}

.p_prof{


    color: #003F91;

    background-color: #FFFFFF;

    padding: 5px;

    border-radius: 5px;
}

.p_data{

font-size: 0.95em;

color: #FFFFFF;

}


.orders{


    display: grid;

    justify-items: center;

    align-items: center;

    grid-auto-flow: row;

}

.orders>.header_tag{

    display: grid;

    margin-top: 10px;

    margin-bottom: 10px;


}

.orders>.header_tag>.incomp_order{


}

.completed_orders{
    display: grid;

    justify-items: center;

    align-items: center;

    grid-auto-flow: row;

}

.completed_orders>.header_tag{
   
    display: grid;
    
    margin-top: 10px;

    margin-bottom: 10px;

}

.completed_orders>.header_tag>.comp_order{



}
</style>