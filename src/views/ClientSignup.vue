<template>
    <div>
        <page-header></page-header>
        <client-signup-component></client-signup-component>
        <page-footer></page-footer>
    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import ClientSignupComponent from '@/components/ClientSignupComponent.vue';
import PageFooter from '@/components/PageFooter.vue';
    export default {
        
        components:{

            PageHeader,
            ClientSignupComponent,
            PageFooter
        }
    }
</script>

<style scoped>

</style>