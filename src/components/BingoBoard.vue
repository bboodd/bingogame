<script setup>

import { computed, defineProps, ref, toRefs } from 'vue'

const props = defineProps({
  board : {
    type: [Object, null],
    required: true
  },
  maxLength: Number
})

const bingoBoolean = computed(() => {
  const temp = []

  for(let i=0;i<props.maxLength;i++){
    temp.push(false)
  }

  return temp
})

const update = (num) => {


}

const checkBingo = () => {

}

</script>

<template>
  <v-container class="bingo-container">
    <v-col v-for="(number, idx) in board.value" :key="idx" :ref="'bingo_'+number">
        <v-row class="bingo" v-for="(num, idx) in number" :key="idx" :ref="'bingo_'+num">
          {{ num }}
        </v-row>
    </v-col>
      {{ bingoBoolean }}
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
    height: 50px;
    font-size: 30px;
    justify-content: center;
    align-items: center;
  }
}
</style>