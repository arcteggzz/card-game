<template>
  <main class="flex flex-col justify-center items-center py-8 space-y-8">
    <h1 class="text-[2.25rem] font-[700] text-[#101828] leading-[60px]">Vue Card Game</h1>
    <p class="text-[1.25rem] font-[400] text-[#667085] leading-[30px]">Match all cards in record time to win.</p>
    <section class="flex space-x-6">
        <div class="flex space-x-6">
            <button :class="buttonStyle">Start</button>
            <button :class="buttonStyle">End</button>
        </div>
        <div class="flex space-x-6">
            <h2 :class="infoStyle">Moves: 12</h2>
            <h2 :class="infoStyle">Time: 4:12</h2>
        </div>
    </section>
  </main>
</template>

<script>

export default {
  name: 'Controls',
  components: {},
  data () {
    return {
        buttonStyle: `text-white font-[500] text-[1rem] bg-[#7F56D9] rounded-[0.5rem] px-[2rem] py-[0.85rem]`,
        infoStyle: `text-[1.2rem] font-[500] text-[#6941C6] leading-[1.5rem] py-[1rem] px-[1rem] bg-[#F9F5FF] rounded-[1rem]`
    }
  }
}
</script>

<style>
</style>
