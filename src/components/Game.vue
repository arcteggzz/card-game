<template>
  <section class="flex justify-center items-center h-[70vh]">
    <GameCard />
    <GameCard />
    <GameCard />
    <GameCard />
  </section>
</template>

<script>
import GameCard from "./GameCard.vue"

export default {
  name: 'Controls',
  components: { GameCard },
}
</script>

<style>
</style>
