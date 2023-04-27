<template>
    <div>

        <page-header></page-header>

        <main class="page_main">
            <section class="section_main">
                <article class="article_main"> 

                    <client-login-component></client-login-component>

                </article>
            </section>
        </main>

    </div>
</template>

<script>
import ClientLoginComponent from '@/components/ClientLoginComponent.vue';

import PageHeader from '@/components/PageHeader.vue';
    export default {
        components:{

            PageHeader,
            ClientLoginComponent,


        }
    }
</script>

<style scoped>

.page_main{


}

.page_main>.section_main{


}

.page_main>.section_main>.article_main{

    
}
</style>