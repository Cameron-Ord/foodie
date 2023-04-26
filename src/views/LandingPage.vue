<template>
    <div class="landing_parent">

        <page-header></page-header>

        <main>
            <section>

                <article>

                    <div>

                        <h1>Did somebody say EatFast</h1>

                    </div>

                    <span>


                        <input placeholder="Enter Your Address" type="text">

                        <input placeholder="Apt/Unit Number" type="text">
                        
                        <input placeholder="Delivery Instructions" type="text">

                        <router-link to="/OrderPage">Find restaurants nearby</router-link>


                    </span>


                </article>
                
            </section>
        </main>

        <page-footer></page-footer>
    

    </div>
</template>

<script>

import PageHeader from '@/components/PageHeader.vue';
import PageFooter from '@/components/PageFooter.vue';

    export default {
        
        components:{

            PageHeader,
            PageFooter
        }
    }
</script>

<style scoped>

</style>