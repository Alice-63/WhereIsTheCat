<template>
   <div class="game-area">
     <p>{{answer}}</p>
       <h1 class="title">Where Is Cat</h1>
       <h4 class="description">Choose a Picture</h4>
       <div class="container">
          <Card 
          class="animate__animated animate__flipInX"
          :class="{'shadow':selectedCard==card.id}"
          @click.native="selectedCard=card.id"
          v-for="(card,index) in cards" 
          :key="card +index" 
          :card="card"></Card>
          
       </div>
       <div class="container">
           <component 
           @click.native="showCard(answer)"
           :card="answer"
           :is="activeCard"
           class="animate__animated animate__flipInY"
           ></component>
          
       </div>
   </div>
</template>
<script>
import Card from './Card.vue';
import DefaultCard from './DefaultCard.vue'
import {eventBus} from '../main'
export default {
    components:
    {
        Card,
        DefaultCard
    },
    data(){
        return{
            selectedCard:null,
            activeCard:"DefaultCard",
            answer:{},
            number:0,
            cards:[
                {id:0,component:"Card",image:"/src/assets/card-1.jpg"},
                {id:1,component:"Card",image:"/src/assets/card-2.jpg"},
                {id:2,component:"Card",image:"/src/assets/card-3.jpg"},
                {id:3,component:"Card",image:"/src/assets/card-4.jpg"},
                {id:4,component:"Card",image:"/src/assets/card-5.jpg"}
            ]
        }
    },
    created(){

        let answer=Math.ceil(Math.random()*this.cards.length);
        this.answer=this.cards[answer-1]
       
    },
    methods:
    {
        showCard(answer){
            if(this.selectedCard==null)
            {
                alert("Please select a picture!")
            }
            else{
                this.activeCard=answer.component
              setTimeout(()=>{
                    
                if(answer.id==this.selectedCard)
                {
                    eventBus.$emit("isCorrectEvent","Celebrate")
                }
                else{
                    this.number++
                    if(this.number==1)
                   {eventBus.$emit("isCorrectEvent","Failure")}
                   number=0
                }
              },1000)
            }
            
        }
    }
}


</script>
<style scoped>

.title
{
    text-align: center;
    font-family: sans-serif;
    color: rosybrown;
}

.description
{
    color: grey;
    text-align: center;
}

.container
{
    display: flex;
    justify-content: center;
    align-content: center;
    margin-top: 50px;
}
.shadow
{
    box-shadow: 0 5px 20px #30969f !important
}


</style>