<script setup>
import {ref, onMounted,watch, watchEffect} from 'vue';
const props =defineProps(["horse1","horse2","horseMoveBegin1","horseMoveBegin2","startGame", "showWinBoard"])
const emit = defineEmits (["update:horse1","update:horse2","update:horseMoveBegin1","update:horseMoveBegin2","stopHorse1","stopHorse2","showWinBoard"])


const horseMovePaddingImg01 = Math.floor(Math.random()*101);
const horseMovePaddingImg02 = Math.floor(Math.random()*101);
const horseMovePadding1 = ref(horseMovePaddingImg01);
const horseMovePadding2 = ref(horseMovePaddingImg02);
const horseMoveBegin1 = ref(horseMovePaddingImg01);
const horseMoveBegin2 = ref(horseMovePaddingImg02);
const moveImg01 = () => {
    emit("update:horseMoveBegin1", horseMoveBegin1.value)
    const timer = setInterval(() => {
        horseMovePadding1.value++
        emit("update:horse1", horseMovePadding1.value)
        if (horseMovePadding1.value > 840){  
            clearInterval(timer) 
            emit("stopHorse1", true)    
            emit("showWinBoard", true)
            
         }
    },10)
   
}
 const moveImg02 = () => {
    emit("update:horseMoveBegin2", horseMoveBegin2.value)
    const timer = setInterval(() => {
        horseMovePadding2.value++
        emit("update:horse2", horseMovePadding2.value)
        if (horseMovePadding2.value > 840){  
           clearInterval(timer)  
           emit("stopHorse2", true)  
           emit("showWinBoard", true)    
         }
    },10)
   
}



watchEffect( ()=>{
    if( props.startGame){
        moveImg01()
        moveImg02()
    }
    
})

</script>

<template>  
<div>
    <div>
        <img class="img01" src="src/Desing/horse.gif"  width="200" height="200" :style= "`padding-left: ${horseMovePadding1}px;`"/> 
    </div>
    <br/><br/><br/><br/>
    <div>
        <img class="img02" src="src/Desing/horse.gif"  width="200" height="200" :style= "`padding-left: ${horseMovePadding2}px;`"/> 
    </div>
</div>   
      
</template>

<style scoped>
.img01{
padding-left: 0px;
}
.img02{
padding-left: 0px;
}

</style>
