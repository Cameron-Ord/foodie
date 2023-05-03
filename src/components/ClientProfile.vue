<template>
    <div>
        <main class="page_main">
            <section class="section_main">
                <article class="article_1">
                    <span class="article_1_span_2">

                        <h1>Welcome, {{ client_data_holder[`username`] }}</h1>

                        <h1>Account info:</h1>

                        <img v-bind:src="client_data_holder[`image_url`]">

                        <p>Email: {{ client_data_holder[`email`] }}</p>

                        <p>First-name: {{ client_data_holder[`first_name`] }}</p>

                        <p>last-name: {{ client_data_holder[`last_name`] }}</p>

                        <p>username: {{ client_data_holder[`username`] }}</p>

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

                    <span class="article_1_span_4">

                        <h1>Account settings:</h1>

                        <input placeholder="enter your password to delete your account" type="password" ref="delete_account">

                        <button @click="delete_profile">Delete Account</button>


                    </span>

                </article>

                <article class="orders">


                    <h1>Current Orders</h1>

                    <span v-for="(order, i) in incomplete_orders" :key="i">

                        <div v-if="incomplete_orders[i][`is_complete`] != 1">
                    
                        <h1>{{ order.name }}</h1>
                    
                        <p>{{ order.order_id }}</p>
                    </div>
                    </span>

                </article>

                <article class="completed_orders">

                    <h1>Order History</h1>

                    <span v-for="(order, i) in completed_orders" :key="i">

                    <div v-if="completed_orders[i][`is_complete`] != 0">
                    
                    <h1>{{ order.name }}</h1>
                    
                    <p>{{ order.order_id }}</p>

                    </div>

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

            incomplete_orders:[],

            completed_orders:[]
        }
    },



    methods: {

        delete_profile(){

            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `DELETE`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data:{

                    password: this.$refs[`delete_account`].value,
                }
                
            }).then((response)=>{

                response;

                this.$router.push(`/`);
            }).catch((error)=>{

                error;
            })


        },


        change_email(){

            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data:{

                    email: this.$refs[`email_change`].value,
                }

            }).then((response)=>{

                response;

            }).catch((error)=>{

                error;

            });

        },

        change_username(){
            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data:{

                    username: this.$refs[`username_change`].value,
                }

            }).then((response)=>{

                response;

            }).catch((error)=>{

                error;

            });

        },

        change_avatar(){
  
            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data:{

                    image_url: this.$refs[`avatar_change`].value,
                }

            }).then((response)=>{

                response;

            }).catch((error)=>{

                error;

            });

        },

        change_password(){

  
            let client_token = Cookies.get(`client_login_token`);

            axios({

                method: `PATCH`,

                url: `https://foodie.bymoen.codes/api/client`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                    token: client_token,

                },

                data:{

                    password: this.$refs[`password_change`].value,
                }

            }).then((response)=>{

                response;

            }).catch((error)=>{

                error;

            });

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

        axios({

            method:`GET`,

            url: `https://foodie.bymoen.codes/api/client-order`,

            headers:{

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: client_token

            },

            params:{

                is_complete: `false`
            }


        }).then((response)=>{

          response;

          console.log(response);


          for(let i = 0; i < response[`data`].length; i++){

            this.incomplete_orders.push(response[`data`][i])
            
          }
        }).catch((error)=>{

            error;

        });

         axios({

            method:`GET`,

            url: `https://foodie.bymoen.codes/api/client-order`,

            headers:{

                'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                token: client_token

            },

            params:{

                is_complete: "true"
            }


        }).then((response)=>{

          response;

          console.log(response);

          for(let i = 0; i < response[`data`].length; i++){
            this.completed_orders.push(response[`data`][i])

          }


        }).catch((error)=>{

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

    align-items: center;

    justify-items: center;
}

.page_main>.section_main{

    display: grid;

    grid-auto-flow: row;

    align-items: center;

    justify-items: center;

    width: 100%;

}

.page_main>.section_main>.article_1{

    display: grid;

    grid-auto-flow: row;

    align-items: center;

    justify-items: center;

    width: 100%;

}



.page_main>.section_main>.article_1>.article_1_span_2{

display: grid;

grid-template-rows: auto;

align-items: center;

justify-items: center;

grid-template-rows: 10vh 5vh 30vh 5vh 5vh 5vh 5vh;


}

.page_main>.section_main>.article_1>.article_1_span_2>img{

    height: 125px;
    width: 125px;
}

.page_main>.section_main>.article_1>.article_1_span_3{

display: grid;

grid-template-rows: auto;

align-items: center;

justify-items: center;

grid-template-rows: 10vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;
}


.page_main>.section_main>.article_1>.article_1_span_4{

display: grid;

grid-template-rows: auto;

align-items: center;

justify-items: center;

grid-template-rows: 10vh 5vh 5vh;
}
</style>