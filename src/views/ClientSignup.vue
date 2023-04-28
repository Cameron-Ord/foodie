<template>
    <div>
        <page-header></page-header>
        <client-signup-component></client-signup-component>


    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import ClientSignupComponent from '@/components/ClientSignupComponent.vue';
    export default {
        
        components:{

            PageHeader,
            ClientSignupComponent
        }
    }
</script>

<style scoped>

</style>