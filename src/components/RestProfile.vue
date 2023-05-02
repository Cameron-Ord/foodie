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
                        
                        <p>Bio: {{rest_data_holder[`bio`] }}</p>
                        
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

                </article>

                <article class="article_3">

                        <span class="span_1" v-for="(image, i) in menu_get_holder" :key="i">

                      <h2>{{ image[`name`] }}</h2>
                        <img :src="image[`image_url`]">


                      
                        <p>Change Name</p>
                        <input type="text" ref="Name_Box"> 
                        <p>Change Description</p>
                        <input type="text" ref="Desc_Box"> 
                        <p>Change Image</p>
                        <input type="text" ref="Image_Box"> 
                        <p>Change Price</p>
                        <input type="text" ref="Price_Box"> 
  
                        <button :clicked_item="i" ref="product_clicked" @click="edit_product">Edit</button> <button :clicked_item="i" ref="product_clicked" @click="delete_product">Delete</button>

                    </span>

                </article>
              
                <article class="article_4">
              
                    <span class="span_1">
                        
                        <h1>Account Settings:</h1>
                    
                        <input  placeholder="enter your password to delete your account" type="text" ref="delete_acc">
                       

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
    export default {
      
        data() {
            return {
                
                index: 0,


            rest_data_holder: {},

            menu_get_holder: [],

         

           
        }
        },

        methods:{

            delete_account(){

                let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `DELETE`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{


                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        password: this.$refs[`delete_acc`][`value`],

                    }

                }).then((response) => {

                    response;

                }).catch((error) => {

                    error;

                });


            },


            change_email(){

                let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `PATCH`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        email: this.$refs[`change_email`][`value`],
                    }

                }).then((response)=>{
                    
                    response;


                }).catch((error)=>{

                    error;

                });

            },

            change_phone(){

                let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `PATCH`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        phone_number: this.$refs[`change_number`][`value`],
                    }

                }).then((response)=>{
                    
                    response;


                }).catch((error)=>{

                    error;

                });
                
            },

            change_address(){

             let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `PATCH`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        address: this.$refs[`change_address`][`value`],
                    }

                }).then((response)=>{
                    
                    response;


                }).catch((error)=>{

                    error;

                });

            },

            change_bio(){

            let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `PATCH`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        bio: this.$refs[`change_bio`][`value`],
                    }

                }).then((response)=>{
                    
                    response;


                }).catch((error)=>{

                    error;

                });


            },

            change_banner(){

            let restaurant_token = Cookies.get(`rest_login_token`);

                axios({

                    method: `PATCH`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                        
                        token: restaurant_token,
                    },

                    data:{

                        banner_url: this.$refs[`change_banner`][`value`],
                    }

                }).then((response)=>{
                    
                    response;


                }).catch((error)=>{

                    error;

                });



            },


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

                  
                    response;

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

                  response;

                }).catch((error)=>{

                    error;

                });
            }

        },




        mounted(){

       

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

.article_1{
    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;
}

.article_1>.article_1_div{

    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 10vh 1fr;

    width: 100%;
}

.article_1>.article_1_div>img{

    width: 100%;

    object-fit: cover;

}

.article_1>.span_1{

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;
    
    grid-template-rows: 7vh 7vh 7vh 1fr 7vh;

    width: 100%;

}

.article_1>.span_2{

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;
    
}
.article_2{
 

    display: grid;

    justify-items: center;

    align-items: center;
}

.article_2>.span_1{


    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;

}
.article_3{
    display: grid;

    justify-items: center;

    align-items: center;

    grid-auto-flow: row;
}

.article_3>.span_1{

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 10vh 25vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh 5vh;
 

}

.article_3>.span_1>img{

    width: 125px;
    height: 125px;

}
.article_4{
    display: grid;
    justify-items: center;

    align-items: center;

    text-align: center;
}
.article_4>.span_1{


    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    grid-template-rows: 15vh 5vh 5vh;
}
</style>