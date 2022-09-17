<template>
  <div v-if="showBlock">
    <button :disabled="disabled" @click="submitPoint">
      Click on me now ~!
    </button>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  export default defineComponent({
    props: {
      delay: {
        type: Number,
        required: true,
      },
      disabled: {
        type: Boolean,
        required: false,
        default: false,
      },
    },
    emits: ['submit'],
    data() {
      return {
        startedTime: 0,
        showBlock: false,
      }
    },
    mounted() {
      setTimeout(() => {
        this.showBlock = true
      }, this.delay)
    },
    updated() {
      this.startedTime = new Date().getTime()
    },
    methods: {
      submitPoint() {
        const diff = new Date().getTime() - this.startedTime
        this.$emit('submit', diff)
      },
    },
  })
</script>

<style scoped>
  button {
    padding: 100px 150px;
    border: none;
    border-radius: 15px;
    background-color: beige;
    outline: none;
  }
  button:hover {
    background-color: bisque;
  }
</style>
