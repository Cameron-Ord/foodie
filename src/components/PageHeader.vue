<template>
    <div class="header_parent">
        <header class="page_header">

            <span class="header_span">

                <h1>LOGO</h1>

                <div class="hero_div">
                    

                 <router-link to="/RestaurantLogin">Restaurant signup</router-link>


                <router-link to="/ClientSignup">Sign up</router-link>

            </div>
            </span>

        </header>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>

.page_header{

    display: grid;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    justify-items: center;

    align-items: center;

}
.page_header>.header_span{

    display: grid;

    grid-template-columns: 1fr 1fr;

    justify-items: start;

    align-items: center;
}

.page_header>.header_span>.hero_div{


    display: grid;

    grid-template-columns: 1fr 1fr;

    justify-items: end;

    align-items: center;

}

</style>