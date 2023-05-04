<template>
    <div>
        <footer class="page_footer">

            <span>

            <nav>

                <p>text</p>
                <p>text</p>
                <p>text</p>
                <p>text</p>

            </nav>

          
            
           
            <nav>

                <p>text</p>
                <p>text</p>
                <p>text</p>
                <p>text</p>
                
            </nav>


            </span>
            
        </footer>

    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
.page_footer{

    display: grid;

    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

    background: #003F91;

    align-items: center;

    justify-items: center;

    min-height: 10vh;

    color: #FFFFFF;

}

.page_footer>span{

    display: grid;


    grid-template-columns: 35vw 35vw;

    justify-items: center;

    align-items: center;


}

.page_footer>span>nav{

    display: grid;

    grid-template-columns: 15vw 15vw ;

    justify-items: center;

    align-items: center;
}

</style>