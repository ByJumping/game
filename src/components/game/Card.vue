<template>
  <div v-if="win">
    <h1 class="win">Победа</h1>
  </div>
    <div v-else class="game__wrapper">
      <div :class="{active: active.includes(i)}" v-for="(image,i) in selectedImage" class="game__wrapper_item" :key="i" @click="showCard(image, i)">
        <img :src="image.path" alt="" :class="{show: show}"/>
      </div>
    </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    images: {
      type: Object,
      default: () => {}
    },
  },
  watch: {
    active: {
      deep: true,
      handler() {
        if(this.active.length === this.images.length) {
          this.win = true
        }
      }
    }
  },
  data() {
    return {
      active: [],
      activeCard: [],
      selectedImage: null,
      show: true,
      win: false,
    }
  },
  created() {
    this.selectedImage = this.shuffle(this.images)
  },
  mounted() {
    setTimeout(() => {
      this.show = false
    }, 5000)
  },
  methods: {
    showCard(image, i) {
      if (this.activeCard.includes(image.id) || this.activeCard.length === 0) {
        this.active.push(i)
        this.activeCard.push(image.id)
      }
      if(!this.activeCard.includes(image.id)) {
        this.active.pop()
        this.activeCard = []
      }
      if(this.activeCard.length === 2) {
        this.activeCard = []
      }
    },
    shuffle(arr) {
      for (let i = arr.length - 1; i > 0; --i) {
        const pos = Math.floor(Math.random() * (i + 1));
        const t = arr[pos];
        arr[pos] = arr[i];
        arr[i] = t;
      }
      return arr;
    }
  }
}
</script>

<style scoped>

</style>