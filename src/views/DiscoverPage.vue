<template>
    <div>

        <page-header></page-header>

        <main class="page_main">
            <section class="section_main">
                <article class="page_article_1">
                    <span class="rest_span" v-for="(restaurant, i) in restaurants" :key="i"> 

                        <h1>{{ restaurant[`name`] }}</h1>

                        <img :src="restaurant[`banner_url`]">

                        <p> {{ restaurant[`phone_number`] }}</p>

                        <p>{{ restaurant[`address`] }}</p>

                        <p class="bio_p">{{ restaurant[`bio`] }}</p>


                        <button :clicked_rest="i" @click="rest_chose" ref="button_clicked">view menu</button>

                    </span>
                </article>
            </section>
        </main>

    </div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';
import PageHeader from '@/components/PageHeader.vue';
     export default {


        components:{

            PageHeader

        },


        data() {
            return {
               restaurants: [],
            }
        },

        methods:{

            rest_chose(details){


                this.$refs[`button_clicked`] = details.currentTarget;
              
                let button_clicker = this.$refs[`button_clicked`].getAttribute(`clicked_rest`);

                let restaurant = this.restaurants[button_clicker];

                Cookies.set(`restaurant_selected`, restaurant[`restaurant_id`]);

                this.$router.push(`/PublicPage`);

            }
        },

        mounted(){

            axios({

                method: `GET`,

                url:`https://foodie.bymoen.codes/api/restaurants`,

                headers:{

                    'x-api-key': `qK2iR1gTkkAjPH0kfGDY`
                },

            }).then((response)=>{

                response;

                for(let i = 0; i < response[`data`].length; i = i +1){

                    

                    this.restaurants.push(response[`data`][i]);

       
                }


            }).catch((error) =>{

                error;

            })
        
       
        
        }

    }
</script>

<style scoped>
.page_main{

    display: grid;

    min-height: 80vh;

    justify-items: center;
    
    align-items: center;
}

.page_main>.section_main{


    display: grid;

    justify-items: center;
    
    align-items: center;

    width: 100%;
}

.page_main>.section_main>.page_article_1{

    display: grid;

    justify-items: center;
    
    align-items: center;

    grid-auto-flow: row;
}

.page_main>.section_main>.page_article_1>.rest_span{

    display: grid;

    justify-items: center;
    
    align-items: center;

    text-align: center;

    grid-template-rows: 10vh 25vh 5vh 5vh 1fr 5vh;

    width: 80%;

    margin-top: 25px;

    margin-bottom: 25px;

}

.page_main>.section_main>.page_article_1>.rest_span>img{

    width: 125px;
    height: 125px;



}

.page_main>.section_main>.page_article_1>.rest_span>p{

    width: 75%;
}

.page_main>.section_main>.page_article_1>.rest_span>h1{

}


.page_main>.section_main>.page_article_1>.rest_span>button{


}

.bio_p{

    margin-top: 10px;
    margin-bottom: 10px;
}
</style>