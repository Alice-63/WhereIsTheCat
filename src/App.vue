<template>

  
<div>
    
<component
@click="activeComponent=$event"
:is="activeComponent"
class="animate__animated animate__backInDown"
:key="mainComponent"
></component>
<canvas id="canvas" :key="canvas" v-show="activeComponent=='Celebrate'"></canvas>
</div>
</template>
<script>
import GameCard from "./components/GameCards.vue"
import Failure from "./components/Failure.vue"
import Celebrate from "./components/Celebrate.vue"
import {eventBus} from './main'



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
    },
    created()
    {
        eventBus.$on("isCorrectEvent",(el)=>{
            this.activeComponent=el
        })
    }
}
</script>
<style>
body{
    font-family: sans-serif;
}

</style>
