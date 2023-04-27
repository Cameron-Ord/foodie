<template>
    <div>
        <header class="page_header">


            <nav class="header_span">


                <button @click="make_active" class="hamburger">
                    <div class="bar"></div>
                </button>

                <router-link to="/" class="home_nav"><h1>DEV.</h1></router-link>

            </nav> 


        </header>
        <nav class="mobile_nav">
            <router-link to="/ClientSignup" class="nav_menu">Sign-up</router-link>
            <router-link to="/Login" class="nav_menu">Log-in</router-link>
            <router-link to="/RestaurantSignup" class="nav_menu">Add your restaurant</router-link>
            <router-link to="/RestaurantLogin" class="nav_menu">Restaurant Log-in</router-link>
        </nav>
    </div>
</template>

<script>
    export default {

        methods:{


            make_active(){

                let menu_btn = document.querySelector(`.hamburger`);

                let mobile_menu = document.querySelector(`.mobile_nav`);


                menu_btn.classList.toggle(`is-active`);

                mobile_menu.classList.toggle(`is-active`);
            }

        },
        
        mounted(){

             
        }
    }
</script>

<style scoped>

.page_header{

display: grid;

grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

place-items: center;

align-items: center;

min-height: 10vh;

background-color: #262626;

color: white;
}


.page_header>.header_span{

display: grid;

align-items: center;

grid-template-columns: 3fr 1fr;

}

.hamburger{
    position: relative;

    display: block;
    width: 35px;
    height: 35px;
    cursor: pointer;

    appearance: none;
    background: none;
    outline: none;
    border: none;
}
.hamburger>.bar, .hamburger::after, .hamburger::before{
 
    content: '';
    display: block;
    width: 100%;
    height: 5px;
    background-color: white;
    
    margin-top: 6px;
    margin-bottom: 6px;
    transition: 0.4s;
}

.hamburger.is-active::before{

    transform:rotate(-45deg) translate(-8px, 6px);
}

.hamburger.is-active::after{

transform:rotate(45deg) translate(-9px, -8px);
}

.hamburger.is-active .bar{

    opacity: 0;
}

.mobile_nav{

    position: fixed;
    top:10vh;
    right:100%;
    width: 100%;
    min-height: 100vh;
    display: block;
    z-index: 98;
    background-color: #262626;
    padding-top: 120px;
    transition: 0.4s;
}

.mobile_nav.is-active{

    right: 0;
}

.mobile_nav>.nav_menu{



    display: block;

    text-align: center;

    margin: 0 auto 16px;

    width: 100%;

    max-width: 200px;

    padding: 12px 16px;

    background-color: white;

    color: black;

    text-decoration: none;
}

.home_nav{

    text-decoration: none;
    color: white;
}
</style>