<script setup>

import { defineProps } from 'vue'

defineProps({
  board : {
    type: [Object, null],
    required: true
  }
})

</script>

<template>
  <v-container class="bingo-container">
    <v-sheet class="bingo" v-for="(number, idx) in board.value" :key="idx" :ref="'bingo_'+number">
        {{ number }}
    </v-sheet>
  </v-container>
</template>

<style lang="scss" scoped>
.bingo-container{
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  .bingo{
    flex: 0 0 33%;
    border: 1px solid #ced3d6;
    display: flex;
    height: 100px;
    font-size: 30px;
    justify-content: center;
    align-items: center;
  }
}
</style>