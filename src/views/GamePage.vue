<template>
    <div>

        <h1>{{ welcome_user }}</h1>
        <p>{{ unwanted }}</p>

        <game-button></game-button>

        <!--importing components-->

        <score-board></score-board>

    </div>
</template>

<script>

import Cookies from 'vue-cookies';
import GameButton from '@/components/GameButton.vue';
import ScoreBoard from '@/components/ScoreBoard.vue';

    export default {
        

        components:{

            GameButton,
            ScoreBoard


        },

        data() {
            return {
                
               
                //some variables that are used to display messages when they become defined//

                unwanted: undefined,

                welcome_user: undefined,
            }
        },


        methods:{


        },

        created(){




        },

        mounted(){


            //updates on page load//
            

            //checks if the user is logged in on page load, if user is not logged in, returns them to login page//

                    let login_status = Cookies.get(`login_token`);

                    let login_parse = JSON.parse(login_status);

            

                    if(login_parse === "logged in"){

                     

                       this.welcome_user = `Welcome, user`
                        

                    }else{

                     
                        this.unwanted = "YOU AREN'T LOGGED IN, BEGONE MONSTER!!!";


                        this.$router.push(`/`);

                    }
        }
    }
</script>

<style scoped>

</style>