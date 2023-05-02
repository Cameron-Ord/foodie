<template>
    <div>

        <page-header></page-header>

                    <shopping-cart-c></shopping-cart-c>
             


    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import ShoppingCartC from '@/components/ShoppingCartC.vue';
import Cookies from 'vue-cookies';

    export default {
        

        Cookies,

        components:{
            PageHeader,
            ShoppingCartC
        }
    }
</script>

<style scoped>
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

    
    width: 100%;

}
</style>