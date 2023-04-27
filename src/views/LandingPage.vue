<template>
        <div class="landing_parent">

            <page-header></page-header>

            <main class="page_main">

                <section class="section_main">

                    <article class="landing_article">

                        <div> <h1>did somebody say eatfast</h1></div>

                        <span class="landing_span">

                            <input placeholder="Enter Your Address" type="text">

                            <input placeholder="Apt/Unit Number" type="text">

                            <input placeholder="Delivery Instructions" type="text">


                        </span>

                        <nav>

                            <router-link to="/OrderPage">Find restaurants nearby</router-link>

                        </nav>

                    </article>

                </section>

            </main>




        </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';

export default {

    components: {

        PageHeader

    }
}
</script>

<style scoped>
.page_main{

    display: grid;

    align-items: center;

    justify-items: center;

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

.page_main>.section_main{
    display: grid;

    align-items: center;

    justify-items: center;

    width: 100%;
    
}

.page_main>.section_main>.landing_article{
    display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 1fr 1fr 1fr;

    width: 100%;
}
.page_main>.section_main>.landing_article>.landing_span{

        display: grid;

    align-items: center;

    justify-items: center;

    grid-template-rows: 25px 25px 25px;

    width: 85%;
}
</style>