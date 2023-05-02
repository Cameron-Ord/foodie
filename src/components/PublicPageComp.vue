<template>
    <div>
    <article class="article_1">
    <span class="span_rest">

        <div>

        <h1>{{ restaurant_object[`name`] }}</h1>

      <img :src="restaurant_object[`profile_url`]">

    </div>

      <p>{{ restaurant_object[`city`] }}</p>

      <p>{{ restaurant_object[`address`] }}</p>
    
      <p>{{ restaurant_object[`phone_number`] }}</p>

      <p>{{ restaurant_object[`bio`] }}</p>


    </span>
</article>
<article class="article_2">

    <span class="span_menu" v-for="(menu_item, i) in rest_menu" :key="i">

        <h1>Menu Items:</h1>

        <h4>{{ menu_item[`name`] }}</h4>

        <img :src="menu_item[`image_url`]">

        <p>{{ menu_item[`price`] }}</p>

        <button @click="add_to_cart" ref="button_clicked" :clicked_menu_item="i">Add to cart</button>

    </span>

</article>
</div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {
        

        data() {
            return {
               restaurant_object: {},

               rest_menu: [],

               menu_items: []
            }
        },

        methods:{

            add_to_cart(details, menu_item){

                this.$refs[`button_clicked`] = details.currentTarget;

                let button_clicker = this.$refs[`button_clicked`].getAttribute(`clicked_menu_item`);

                menu_item = this.rest_menu[button_clicker];

                this.menu_items.push(menu_item);

                Cookies.set(`menu_item_added`, this.menu_items);



                console.log(this.menu_items);

            }

        },

        mounted(){


            let chosen_restaurant_id = Cookies.get(`restaurant_selected`);

            if(chosen_restaurant_id !== undefined){

                axios({

                    method: `GET`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                    },

                    params:{

                        restaurant_id: chosen_restaurant_id

                    }


                }).then((response)=>{

 
                    this.restaurant_object = response[`data`][0];

                  

                }).catch((error)=>{

                    error;

                    console.log(`API failure`);
                });


            }

            if(chosen_restaurant_id !== undefined){

            axios({

                method: `GET`,

                url: `https://foodie.bymoen.codes/api/menu`,

                
                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`,
                    },

                    params:{

                        restaurant_id: chosen_restaurant_id

                    }


            }).then((response)=>{

                response;

                for (let i = 0; i < response[`data`].length; i++){

                    this.rest_menu.push(response[`data`][i]);
                }

           

            }).catch((error)=>{

                error

            })
        }


        }
    }
</script>

<style scoped>

.article_1{

    display: grid;

    grid-auto-flow: row;

    justify-items: center;

    align-items: center;

    text-align: center;

}

.article_1>.span_rest{


    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 1fr 5vh 5vh 5vh 10vh;

    
}


.article_1>.span_rest>p{

    width: 75%;
}

.article_1>.span_rest>div{

    display: grid;

    grid-template-rows: 5vh 1fr;

    align-items: center;

    justify-items: center;
}

.article_1>.span_rest>div>img{

    width: 100%;
    object-fit: cover;
    
}

.article_2{

    display: grid;

    grid-auto-flow: row;

    justify-items: center;

    align-items: center;

    text-align: center;
}


.article_2>.span_menu{


    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 10vh 10vh 20vh 5vh;

}

.article_2>.span_menu>img{

    height: 125px;
    width: 125px;
}
</style>