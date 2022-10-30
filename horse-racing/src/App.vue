<script setup>

import {ref} from 'vue';
import Horse from './components/horse/Horse.vue';
import Button from './components/button/Button.vue';
import Announcement from './components/announcement/Announcment.vue';
import Boards from './components/board/Board.vue';

const startGame = ref(false);
const showWinBoard = ref(false);
const horse1 = ref();
const horse2 = ref();
const stopHorse1 = ref(false);
const stopHorse2 = ref(false);
const showHorse = ref(false);
const horseMoveBegin1 = ref();
const horseMoveBegin2 = ref();
const stopHorse1Handler = (stop)=> {
  stopHorse1.value = stop
}
const stopHorse2Handler = (stop)=> {
  stopHorse2.value = stop
}
const clickHandler = () => {
  startGame.value = true
  showHorse.value = true
}
const showWinBoardHandler =(shows) => {
  showWinBoard.value = shows
}

</script>

<template >
<div class="main">
  <div class="header">      
      <h1 class="headerText"> WELCOME TO HORSE RACING</h1>
      <Button :stopHorse1="stopHorse1" :stopHorse2="stopHorse2" :startGame="startGame"  ></Button>
      <button type="button" class="startButton" @click="clickHandler">Start</button>    
      <button class="startButton" onclick="window.location.reload(false)">Refresh</button>
  </div>
  <div class="container" >
        <br/><br/><br/><br/>
        <div v-if="showWinBoard==true">
          <Boards :horseMoveBegin1="horseMoveBegin1" :horseMoveBegin2="horseMoveBegin2"></Boards>
        </div>
        <div v-show="showWinBoard==false">
          <div v-if="showHorse==true">
            <Horse v-model:horse1="horse1" v-model:horse2="horse2" @showWinBoard="showWinBoardHandler" 
                      @stopHorse1="stopHorse1Handler" @stopHorse2="stopHorse2Handler" :startGame="startGame"
                        v-model:horseMoveBegin1="horseMoveBegin1" v-model:horseMoveBegin2="horseMoveBegin2">
            </Horse>  
          </div>
        </div>  
  </div>
  <Announcement :horse1="horse1" :horse2="horse2"></Announcement>
</div>

</template>

<style scoped>
.main{
  width: 1000px;
  height: 1200px;
  position: relative;
  margin: auto; 
  margin-top: 35px;
  z-index: 2;
  background-image: url("src/Desing/horseCool.jpg");
  background-position: center; 
  background-repeat: no-repeat; 
  background-size: cover; 
}
.header{
  width: 100%;
  height: 300px;
  background-color: transparent;
}
.headerText{
color: rgb(220, 223, 231);
text-align: center;
font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
font-style:italic;
font-weight: bold;
padding-top: 55px;

}
.startButton{
background-color:rgb(82, 180, 110);
color: white;
padding: 15px 32px;
text-align: center;
display: inline-block;
font-size: 24px;
font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
font-style:italic;
font-weight: bold;
margin-left: 410px;
width: 200px;
align-content: center;
border-radius: 50%;

}
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

.container{
width: 950px;
height: 700px;
background-color:transparent;
position: relative;
margin-left: 22px; 
margin-top:60px;

}
</style>

