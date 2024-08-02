<script setup>
import { ref, reactive } from "vue"
import BingoPlayer from "./BingoPlayer.vue";
import BingoBoard from "./BingoBoard.vue";

const maxNumber = 15;
const maxLength = 9;

const playerList = reactive([])
const callHistory = reactive([])

const addPlayer = () => {

  if(playerList.length > 9){
    alert("플레이어의 숫자는 최대 10명 입니다.")
    return false
  }

  const player = ref(makeRandomNumbers())
  playerList.push(player)

}

const makeRandomNumbers = () => {

  const randomNumbers = []
  
  while(randomNumbers.length < maxLength){
      const num = Math.floor(Math.random() * maxNumber)+1
      if(!randomNumbers.includes(num)){
          randomNumbers.push(num)
      }
  }
  //2차원 배열로 만들기
  const board = []

  for(let i=0;i<maxLength/3;i++){
    const temp = []
    for(let j=0;j<maxLength/3;j++){
      temp.push(randomNumbers[i+j])
    }
    board.push(temp)
  }

  return board
}

const makeRandomNumber = () => {
  return Math.floor(Math.random() * maxNumber) + 1
}

let gameFlag = ref(false)

const gameStart = () => {

  if(playerList.length > 1) gameFlag.value = true
  else alert("게임시작 최소 인원은 2명 입니다.")
}

const callNumber = () => {
  const randomNumber = makeRandomNumber()

  alert(randomNumber)

  callHistory.push(randomNumber)




}

</script>

<template>
    <v-btn class="add-player-btn" @click="addPlayer()">
        플레이어 추가
    </v-btn>
    <v-btn v-if="!gameFlag" @click="gameStart()">게임시작</v-btn>
    <v-btn v-else @click="callNumber()">콜</v-btn>
    {{ callHistory }}

    <v-container class="bg-surface-variant">
    <v-row no-gutrs>
      <v-col
        v-for="(player, playerId) in playerList" :key="playerId"
        cols="12"
        sm="4"
      >
        <v-col v-text="'player'+(playerId+1)"></v-col>
        <v-sheet class="ma-0 pa-0">
            <BingoBoard :board="player" :maxLength="maxLength"/>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>

.add-player-btn{
  text-align: center;
  display: flex;
  width: 15%;
  align-items: center;
  justify-content: center;
  margin: auto;
}
</style>