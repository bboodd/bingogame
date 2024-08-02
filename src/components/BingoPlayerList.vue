<script setup>
import { ref, reactive } from "vue"
import BingoPlayer from "./BingoPlayer.vue";
import BingoBoard from "./BingoBoard.vue";

const maxNumber = 15;
const maxLength = 9;

const playerList = reactive([])

const addPlayer = () => {

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

    return randomNumbers
}

</script>

<template>
    <v-btn class="add-player-btn" @click="addPlayer()">
        플레이어 추가
    </v-btn>

    <v-container class="bg-surface-variant">
    <v-row no-gutrs>
      <v-col
        v-for="(player, playerId) in playerList" :key="playerId"
        cols="12"
        sm="4"
      >
        <v-col v-text="'player'+(playerId+1)"></v-col>
        <v-sheet class="ma-0 pa-0">
            <BingoBoard :board="player"/>
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