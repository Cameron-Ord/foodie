<template>
    <div class="landing_parent">

        <page-header></page-header>

        <main class="page_main">
            <section class="section_main">

                <article class="landing_article">

                    <span class="landing_span">

                        <h1>did somebody say eatfast</h1>

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

    min-height: 80vh;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    justify-items: center;

    align-items: center;

}

.page_main>.section_main{

    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;


}
.page_main>.section_main>.landing_article{

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    width: 100%;

    grid-template-rows: 2fr 1fr;

}



.page_main>.section_main>.landing_article>.landing_span{

    display: grid;

    width: 80%;

    grid-template-rows: 50px 50px 50px 50px;
}
.page_main>.section_main>.landing_article>.landing_span>input{

    display: inline;

    margin-top: 5px;

    margin-bottom: 5px;
}

</style>