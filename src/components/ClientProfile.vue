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

                    <span>

                        <h1>Account settings:</h1>

                        <input placeholder="enter your password to delete your account" type="password" ref="delete_account">

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

    }
}
</script>

<style scoped>

</style>