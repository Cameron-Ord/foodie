<template>
    <div>
        <page-header></page-header>

        <main class="page_main">

            <section class="section_main">
              
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

.page_main{

    display: grid;

    min-height: 80vh;

    justify-items: center;

    align-items: center;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

.page_main>.section_main{


    display: grid;

    justify-items: center;

    align-items: center;
}
</style>