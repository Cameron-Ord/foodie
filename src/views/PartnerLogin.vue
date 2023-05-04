<template>
    <div>

        <page-header></page-header>


                    <restaurant-login-component></restaurant-login-component>

                    <page-footer></page-footer>

    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import RestaurantLoginComponent from '@/components/RestaurantLoginComponent.vue';

import PageFooter from '@/components/PageFooter.vue';

    export default {
        
        components:{
            PageHeader,
            RestaurantLoginComponent,
            PageFooter
        }
    }
</script>

<style scoped>

</style>