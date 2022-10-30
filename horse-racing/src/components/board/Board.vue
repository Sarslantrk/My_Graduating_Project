<script setup>
import {ref , computed} from 'vue';
const props =defineProps(["horseMoveBegin1","horseMoveBegin2"])
</script>

<template>
    <div class="winner_board">
        <div v-if="props.horseMoveBegin1 > props.horseMoveBegin2" >
        <h2 class="winner_text">Gulbatur win</h2>
        </div>
        <div v-if="props.horseMoveBegin1 < props.horseMoveBegin2">
        <h2 class="winner_text">Baturay win</h2>
        </div>
    </div>
</template>

<style scoped>
.winner_board{
    width: 500px;
    height: 490px;
    color: white;
    margin: auto;  
    background-image: url("src/Desing/horseWinner.jpg");
    background-position: center; 
    background-repeat: no-repeat; 
    background-size: cover; 
    text-align: center;
}
.winner_text{
    font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-style:italic;
    font-weight: bold;
    padding-top: 250px;
    color: rgb(124, 124, 50);
}
</style>