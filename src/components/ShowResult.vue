<template>
  <div>
    <h1>⛟ Your time: {{ time }} ms</h1>
    <h1>⛟ Your rank: {{ getRank }}</h1>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  export default defineComponent({
    props: {
      time: { type: Number, required: true },
    },
    computed: {
      getRank() {
        if (this.$props.time <= 250) return 'God'
        else if (this.$props.time <= 300) return 'Robot'
        else return 'Baby'
      },
    },
  })
</script>

<style lang=""></style>
