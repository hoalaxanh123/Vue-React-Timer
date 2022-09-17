<template>
  <div>
    <h1>☢ React timer ☢</h1>
    <button :disabled="isPlaying" @click="gameOn">
      ⛏
      {{ isPlaying ? 'Waiting...' : 'Play' }}🔪
    </button>
  </div>

  <ShowResult v-if="isSubmitted" :time="result" />

  <BlockGame
    v-if="isPlaying"
    :delay="delay"
    :disabled="isSubmitted"
    @submit="submitGame"
  />
</template>

<script lang="ts">
  import BlockGame from './components/BlockGame.vue'
  import ShowResult from './components/ShowResult.vue'
  import { defineComponent } from 'vue'

  export default defineComponent({
    components: { BlockGame, ShowResult },
    data() {
      return {
        delay: 0,
        isPlaying: false,
        isSubmitted: false,
        result: 0,
      }
    },

    methods: {
      gameOn() {
        this.isPlaying = true
        this.isSubmitted = false
        this.delay = 1000 + Math.random() * 2000
      },
      submitGame(result: number) {
        this.isSubmitted = true
        this.isPlaying = false
        this.result = result
      },
    },
  })
</script>

<style scoped>
  button {
    padding: 15px 50px;
    margin: 10px;
    background-color: #00dcff;
    font-weight: bolds;
    border: none;
    outline: none;
  }
  button:hover {
    background-color: #00fcfb;
  }
</style>
