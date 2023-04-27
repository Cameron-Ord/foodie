<template>
    <div>

    </div>
</template>

<script>
import Cookies from 'vue-cookies';
import axios from 'axios';
    export default {
        data() {
            return {
                
            }
        },


        methods:{


        },

        mounted(){


            let restaurant_token = Cookies.get(`rest_login_token`);

            let client_token = Cookies.get(`client_login_token`);

            let client_id_value = Cookies.get(`client_id_token`);

            let rest_id_value = Cookies.get(`rest_login_token`);

            console.log(client_id_value);
            if(client_token !== undefined){

                axios({

                    method: `GET`,

                    url: `https://foodie.bymoen.codes/api/client`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                    },

                    params:{

                        client_id: client_id_value,

                    }
                   
                    
                }).then((response)=>{

                    response;
                    console.log(`client profile api success`);


                }).catch((error)=>{

                    error;

                })



            }else if(restaurant_token !== undefined){

                axios({

                    method: `GET`,

                    url: `https://foodie.bymoen.codes/api/restaurant`,

                    headers:{

                        'x-api-key': `qK2iR1gTkkAjPH0kfGDY`

                    },

                    params:{

                        restaurant_id: rest_id_value,
                    }

                    
                }).then((response)=>{
                    response;
                    console.log(`restaurant profile api success`);


                }).catch((error)=>{

                    error
                });

            }else{

                console.log(`failure`);
            }


        }
    }
</script>

<style scoped>

</style>