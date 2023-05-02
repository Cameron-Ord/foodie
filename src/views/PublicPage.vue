<template>
    <div>
        <page-header></page-header>

        <main>

            <section>
              
                    <public-page-comp></public-page-comp>
                
            </section>
        </main>
        

    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import PublicPageComp from '@/components/PublicPageComp.vue';
    export default {
        

        components:{

            PageHeader,
            PublicPageComp
        }
    }
</script>

<style scoped>

</style>