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

</style>