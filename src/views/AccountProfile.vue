<template>
    <div>
        <page-header></page-header>
    
        <client-profile v-if="client_data != undefined"></client-profile>
        
        <rest-profile v-if="rest_data != undefined"></rest-profile>
    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import ClientProfile from '@/components/ClientProfile.vue';
import RestProfile from '@/components/RestProfile.vue';
import Cookies from 'vue-cookies';
    export default {
      
        components:{

            PageHeader,
            ClientProfile,
            RestProfile
        },

        data() {
            return {
                client_data: undefined,
                rest_data: undefined
            }
        },

        mounted(){

            let client_cookie_data = Cookies.get(`client_login_token`);

            this.client_data = client_cookie_data;

            let rest_cookie_data = Cookies.get(`rest_login_token`);

            this.rest_data = rest_cookie_data;

        }
    }
</script>

<style scoped>

</style>