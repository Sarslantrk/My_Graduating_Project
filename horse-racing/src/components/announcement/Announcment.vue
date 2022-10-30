<script setup>
import {ref , computed} from 'vue';
const props =defineProps(["horse1","horse2"])
</script>

<template>
<div class="header_announcement" >
        <div v-if="props.horse1 > props.horse2">
        <h2 class="announcement_text">Gulbatur is winning</h2>
        <h3 class="announcement_text">Don't forget to place your bets!</h3>
        </div>
        <div v-if="props.horse1 < props.horse2">
        <h2 class="announcement_text">Baturay is winning</h2>
        <h3 class="announcement_text">Don't forget to place your bets!</h3> 
        </div>
</div>
</template>

<style scoped>
.header_announcement{
    width: 1000px;
    height: 140px;
    color: beige;
    background-image: url("src/Desing/board.jpg");
    background-position: center; 
    background-repeat: no-repeat; 
    background-size: cover; 
}
.announcement_text{
    font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-style:italic;
    font-weight: bold;
    padding-top: 5px;
    text-align: center;
    color: rgb(124, 124, 50);
}
</style>

    
