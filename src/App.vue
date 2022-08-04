<template>
  <div class="">
    <Controls @setGameState="setGameState"/>
    <Game v-if="isPlaying" />
  </div>
</template>

<script>
import Controls from "./components/Controls.vue"
import Game from "./components/Game.vue"

export default {
  name: 'App',
  components: { Controls, Game },
  data() {
    return {
      isPlaying: false
    }
  },
  methods: {
    setGameState(gameActive) {
      this.isPlaying = gameActive
    }
  }
}
</script>

<style>
</style>
