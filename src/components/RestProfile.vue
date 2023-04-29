<template>
    <div>
        <main>
            <section>
                <article>
              
                    <span>
                        <h1>Welcome, {{ rest_data_holder[`username`] }}</h1>
                    </span>
                    <span>
                        <h1>Account info:</h1>

                        <img v-bind:src="rest_data_holder[`profile_url`]">

                        <p>Email: {{ rest_data_holder[`email`] }}</p>

                        <p>Address: {{ rest_data_holder[`address`] }}</p>
                        
                        <p>Phone Number: {{ rest_data_holder[`phone_number`] }}</p>
                        
                        <p>Bio: {{rest_data_holder[`bio`] }}</p>
                        
                        <p>Location: {{ rest_data_holder[`city`] }}</p>
                    
                    </span>
                    <span>

                        <h1>Edit your profile:</h1>

                        <p>Change business email:</p>

                        <input placeholder="enter a new email" type="text">

                        <p>Change phone number:</p>

                        <input placeholder="enter a new phone number" type="text">
                    
                        <p>Change address:</p>

                        <input placeholder="enter your new address" type="text">
                    
                        <p>Edit your bio:</p>

                        <input placeholder="write your information here" type="text">
                   
                        <p>Change banner:</p>
                   
                        <input placeholder="upload your image here" type="text">
                   
                   
                    </span>

                    <span>

                        <h1>Add, modify, or remove your menu items:</h1>

                        <p>Name</p>
                        <input type="text" ref="Name_Box"> 
                        <p>Description</p>
                        <input type="text" ref="Desc_Box"> 
                        <p>Image</p>
                        <input type="text" ref="Image_Box"> 
                        <p>Price</p>
                        <input type="text" ref="Price_Box"> 
  
                        <button @click="add_product">Add</button><button @click="edit_product">Edit</button><button @click="delete_product">Delete</button>
                    </span>

                    <span>
                        
                        <h1>Account Settings:</h1>
                    
                        <button>Delete Account</button>
                    
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
                

            rest_data_holder: {},
           
        }
        },

        methods:{

            add_product(){


            },

            edit_product(){


            },

            delete_product(){

            }

        },

        mounted(){


        let restaurant_token = Cookies.get(`rest_login_token`);

        let rest_id_value = Cookies.get(`rest_login_token`);


            if (restaurant_token !== undefined) {

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
                console.log(`restaurant profile api success`);

    
                this.rest_data_holder = response[`data`][0];


            }).catch((error) => {

                error
            });

        }
        }
    }
</script>

<style scoped>

</style>