<template>
    <div>

        <page-header></page-header>

                    <client-login-component></client-login-component>

                    <page-footer></page-footer>

    </div>
</template>

<script>
import ClientLoginComponent from '@/components/ClientLoginComponent.vue';
import PageFooter from '@/components/PageFooter.vue';
import PageHeader from '@/components/PageHeader.vue';
    export default {
        components:{

            PageHeader,
            ClientLoginComponent,
            PageFooter


        }
    }
</script>

<style scoped>

</style>