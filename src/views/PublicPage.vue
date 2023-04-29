<template>
    <div>
        <page-header></page-header>

        <main>

            <section>
                <article>
                    <public-page-comp></public-page-comp>
                </article>
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