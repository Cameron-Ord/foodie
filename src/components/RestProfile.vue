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

                    <article>


                    <span>

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

                    </article>

                    <article>

                        <span v-for="(image, i) in menu_get_holder" :key="i">

                      
                        <img :src="image[`image_url`]">
                      
                        <p></p>
                        <input type="text" ref="Name_Box"> 
                        <p></p>
                        <input type="text" ref="Desc_Box"> 
                        <p></p>
                        <input type="text" ref="Image_Box"> 
                        <p></p>
                        <input type="text" ref="Price_Box"> 
  
                        <button :clicked_item="i" ref="product_clicked" @click="edit_product">Edit</button> <button :clicked_item="i" ref="product_clicked" @click="delete_product">Delete</button>

                    </span>

                    </article>

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
                
                index: 0,


            rest_data_holder: {},

            menu_get_holder: [],

         

           
        }
        },

        methods:{

            add_product(){

                let restaurant_token = Cookies.get(`rest_login_token`);

                let rest_id_value = Cookies.get(`restaurant_id`);

                if(rest_id_value !== undefined){

                    axios({

                    method: `POST`,

                    url: `https://foodie.bymoen.codes/api/menu`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                        token: restaurant_token

                    },

                    data:{


                        name: this.$refs[`Name_Box_Add`][`value`],
                        description: this.$refs[`Desc_Box_Add`][`value`],
                        image_url: this.$refs[`Image_Box_Add`][`value`],
                        price: this.$refs[`Price_Box_Add`][`value`]

                    },


                }).then((response)=>{

                    console.log(response);

                }).catch((error)=>{

                    error;

                    console.log(`MENU API FAILURE`);

                });

                }else{

                    console.log(`restaurant id is undefined`);
                }



            },

            edit_product(details){


                let restaurant_token = Cookies.get(`rest_login_token`);


                this.$refs[`product_clicked`] = details.currentTarget;

                let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

                let image = this.menu_get_holder[button_clicked][`id`]; 
                
                Cookies.set(`selected`, image);

                    axios({

                        method: `PATCH`,

                        url: `https://foodie.bymoen.codes/api/menu`,
            
                        headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                        token: restaurant_token

                    },

                    
                    data:{

                        menu_id: image,
                        name: this.$refs[`Name_Box`][`value`],
                        description: this.$refs[`Desc_Box`][`value`],
                        image_url: this.$refs[`Image_Box`][`value`],
                        price: this.$refs[`Price_Box`][`value`]

                    },


                    }).then((response)=>{

                        response;

                        console.log(`MENU UPDATED`);


                    }).catch((error)=>{

                        error;

                        console.log(`MENU API NOT UPDATED`);

                    })

                    


                
           
                

            },



            delete_product(details){

            
                let restaurant_token = Cookies.get(`rest_login_token`);

                this.$refs[`product_clicked`] = details.currentTarget;

                let button_clicked = this.$refs[`product_clicked`].getAttribute(`clicked_item`);

                let image = this.menu_get_holder[button_clicked][`id`]; 

               

                axios({

                    method: `DELETE`,

                        url: `https://foodie.bymoen.codes/api/menu`,
            
                        headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,

                        token: restaurant_token

                    },

                    data:{

                        menu_id: image,
                    }


                }).then((response)=>{

                  console.log(response)

                }).catch((error)=>{

                    error;

                });
            }

        },




        mounted(){

            console.log(this.menu_image);


        let rest_id_value = Cookies.get(`restaurant_id`);
           
                    axios({

                        method: `GET`,

                        url: `https://foodie.bymoen.codes/api/menu`,

                        headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                    
                        },
                        
                        params:{

                        restaurant_id: rest_id_value,

                        },
                     }).then((response)=>{

                        response;

                        for(let i = 0; i < response[`data`].length; i = i +1){

                            this.menu_get_holder.push(response[`data`][i]);



                            
                           
                        }

                    }).catch((error)=>{

                        error;

                    });
                    
               


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
</script>

<style scoped>

</style>