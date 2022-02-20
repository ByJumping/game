<template>
  <div class="header">
    <h1>Тренируй память</h1>
  </div>
    <TrainingComponent/>
</template>

<script>


import TrainingComponent from "@/components/game/Training";
export default {
  name: 'App',
  components: {
    TrainingComponent,
  }
}
</script>

