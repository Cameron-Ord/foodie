<template>
    <div>
        <header class="page_header">

            <div class="divider">
            <span>

                <h1>DEV.</h1>

            </span>
       

            <nav class="header_span">


                <button @click="make_active" class="hamburger">
                    <div class="bar"></div>
                </button>


            </nav> 

        </div>
        </header>
    </div>
</template>

<script>
    export default {

        methods:{


            make_active(){

                let menu_btn = document.querySelector(`.hamburger`);

                menu_btn.classList.toggle(`is-active`);

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

.page_header>.divider{
    display: grid;

    align-items: center;

    grid-template-columns: 60vw 20vw;
}

.page_header>.divider>.header_span{

display: grid;

align-items: center;

justify-items: center;

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

</style>