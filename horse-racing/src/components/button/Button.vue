<script setup>
import {ref , onMounted} from 'vue';
const props = defineProps(["stopHorse1","stopHorse2","startGame"])
const time = ref(0);

const timerDown = () => {
    const timer = setInterval(() => {
        if(props.startGame){
            time.value++  
            if(props.stopHorse1 && props.stopHorse2){
            clearInterval(timer);
        }}
             
    },1000)
   
}

onMounted( ()=>{
    timerDown()
})

</script>

<template>
    <button type="button" class="timerButton" >{{time}}</button>
</template>

<style scoped>
    .timerButton{
    background-color:rgb(82, 180, 110);
    color: white;
    text-align: center;
    display: inline-block;
    font-size: 24px;
    font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-style:italic;
    font-weight: bold;
    margin-left: 810px;
    width: 100px;
    align-content: center;
    border-radius: 50%;
    }
</style>