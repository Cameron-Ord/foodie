<template>
    <div>

        <page-header></page-header>

        <main>
            <section>
                <article>

   
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

</style>