<template>
 <div class="container">
       <h1>Game Over!</h1>
   <button @click="newGame">New Game</button>
 </div>
</template>
<script>
import {eventBus} from '../main'
export default {
    methods:
    {
        newGame(){
             eventBus.$emit("isCorrectEvent","GameCard")
        }
    }
    
}
</script>
<style scoped>
.container
{
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: darkred;


}
.container h1{
    text-align: center;
    font-size: 333%;
    color: white;
}
.container button{
    width: 200px;
    background-color: #fff;
    color: darkred;
    height: 50px;
    font-size: 20px;
    border-radius: 5px;
    outline: none;
    font-weight: bold;
    cursor: pointer;
}
.container button:hover
{
    background-color: lightgreen;
    color:#fff;
    transition: all .5s;
}
</style>