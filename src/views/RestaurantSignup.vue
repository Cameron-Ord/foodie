<template>
    <div>
           

        <page-header></page-header>

        <restaurant-signup-component></restaurant-signup-component>

    </div>
</template>

<script>


import PageHeader from '@/components/PageHeader.vue';
import RestaurantSignupComponent from '@/components/RestaurantSignupComponent.vue';
import axios from 'axios';
import Cookies from 'vue-cookies';
    export default {

        components:{

    
            PageHeader,
            RestaurantSignupComponent
        },

        Cookies,
        axios
    }
</script>

<style scoped>
</style>