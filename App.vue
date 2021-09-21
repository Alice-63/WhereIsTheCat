<template>

  

<component
:is="activeComponent"></component>

</template>
<script>
import GameCard from "./components/GameCards.vue"
import Failure from "./components/Failure.vue"
import Celebrate from "./components/Celebrate.vue"




export default {
    data(){
        return{
            activeComponent:"GameCard"

        }
    },
    components:
    {
    GameCard,
    Failure,
    Celebrate
    }
}
</script>
<style>
body{
    font-family: sans-serif;
}

</style>
