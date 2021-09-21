<template>
   <div class="game-area">
      
       <h1 class="title">Wo ist Katze</h1>
       <h4 class="description">Wählen Sie Bitte eine Karte aus</h4>
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
           <DefaultCard></DefaultCard>
       </div>
   </div>
</template>
<script>
import Card from './Card.vue';
import DefaultCard from './DefaultCard.vue'
export default {
    components:
    {
        Card,
        DefaultCard
    },
    data(){
        return{
            selectedCard:null,
            answer:{},
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
        console.log(this.answer)
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