<template>
    <div>

        <main class="page_main">
            <section class="section_main">

        <article class="cart_container">

        <span class="product_span" v-for="(item, i) in shopping_cart_items" :key="i">

        <h4>{{ item[`name`] }}</h4>
    
        <img :src="item[`image_url`]">

        <p> ${{ item[`price`] }}</p>

        </span>
        </article>

        <article class="order_container">

            <span class="button_span">

                <button @click="Order">Order</button>

            </span>

        </article>
    </section>
        </main>

        

    </div>
</template>

<script>
import Cookies from 'vue-cookies';
    export default {

        data() {
            return {
               

                shopping_cart_items: undefined
            }
        },
        
        methods:{


            Order(){


            }

        },



        mounted(){

            this.shopping_cart_items = Cookies.get(`food_cart`);
            console.log(this.shopping_cart_items, `cart`)

        }
    }
</script>


<style scoped>

img{
    width: 50px;
    height: 50px;
}
.page_main{

display: grid;

align-items: center;

justify-items: center;

grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

text-align: center;
}

.page_main>.section_main{

display: grid;

align-items: center;

justify-items: center;

grid-template-rows: 1fr 1fr;

width: 100%;

}
.cart_container{

    display: grid;

    align-items: center;

    justify-items: center;

    grid-auto-flow: row;

    width: 100%;



}

.product_span{

    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-columns: 50vw 20vw 20vw;

    margin-top: 10px;

    margin-bottom: 10px;
    

}

.order_container{

    display: grid;

    align-items: center;

    justify-items: center;

    text-align: center;

    width: 100%;

 
}
.order_container>.button_span{

    display: grid;

    align-items: center;

    justify-items: center;

}

</style>