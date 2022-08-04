<template>
  <div class="">
    <Controls />
    <Game />
  </div>
</template>

<script>
import Controls from "./components/Controls.vue"
import Game from "./components/Game.vue"

export default {
  name: 'App',
  components: { Controls, Game }
}
</script>

<style>
</style>
