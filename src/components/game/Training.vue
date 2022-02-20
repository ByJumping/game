<template>
  <div class="game">
    <CardComponent v-if="start" :images="images"/>
      <button v-if="!start" @click="startGame">начать</button>
  </div>
</template>

<script>

import CardComponent from "@/components/game/Card";
import {imagesData} from "@/assets/imagesData";
export default {
  name: "TrainingComponent",
  components: {CardComponent},
  data() {
    return {
      images: imagesData,
      start: false,

    }
  },
  methods: {
    startGame() {
      this.start = true
    },
  }
}
</script>

<style scoped>

</style>