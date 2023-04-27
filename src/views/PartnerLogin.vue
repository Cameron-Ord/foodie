<template>
    <div>

        <page-header></page-header>

        <main class="page_main">
            <section class="section_main">
                <article class="article_main"> 

                    <restaurant-login-component></restaurant-login-component>

                </article>
            </section>
        </main>

    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import RestaurantLoginComponent from '@/components/RestaurantLoginComponent.vue';
    export default {
        
        components:{
            PageHeader,
            RestaurantLoginComponent
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