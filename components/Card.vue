<template>
 <div class="card">
               <img :src="card.image" alt="">
</div>
    
</template>

<style scoped>
.card
{
 width: 200px;
 height: 232px;
 border-radius: 5px;
 border: 1px solid #666;
 transition: box-shadow .5s;
 margin-left: 15px;
}
.card:first-child
{
    margin-left: 0;
}
.card:hover
{
    box-shadow: 0px 5px 20px #666;
    transition: box-shadow .5s;

}
</style>
<script>
export default {
    props:
    {
        card:Object
    }
}
</script>