<template>
  <main class="flex flex-col justify-center items-center py-8 space-y-8 h-[30vh]">
    <h1 class="text-[2.25rem] font-[700] text-[#101828] leading-[60px]">Vue Card Game</h1>
    <p class="text-[1.25rem] font-[400] text-[#667085] leading-[30px]">Match all cards in record time to win.</p>
    <section class="flex space-x-6">
        <div class="flex space-x-6">
            <button :class="buttonStyle" @click="startGame">Start</button>
            <button :class="buttonStyle" @click="endGame">End</button>
        </div>
        <div class="flex space-x-6">
            <h2 :class="infoStyle">Moves: {{ moveCounter }}</h2>
            <h2 :class="infoStyle">PairsFound: {{ pairsFound }}</h2>
            <h2 :class="infoStyle">Time: {{ timeSpentText }}</h2>
        </div>
    </section>
  </main>
</template>

<script>
import { eventBus } from "../main";

export default {
  name: 'Controls',
  components: {},
  data () {
    return {
        buttonStyle: `text-white font-[500] text-[1rem] bg-[#7F56D9] rounded-[0.5rem] px-[2rem] py-[0.85rem]`,
        infoStyle: `text-[1.2rem] font-[500] text-[#6941C6] leading-[1.5rem] py-[1rem] w-[10rem] bg-[#F9F5FF] rounded-[1rem] text-center`,
        gameActive: false,
        timeSpentNum: 0,
        timeSpentText: `00:00`,
        pairsFound: 0,
        moveCounter: 0
    }
  },
  methods: {
    startGame() {
      this.gameActive = true
      this.$emit('setGameState', this.gameActive)
      setInterval(()=>{
        if(this.gameActive){
          this.timeSpentNum++
          const divisor_for_minutes = this.timeSpentNum % (60 * 60);
          const minutes = Math.floor(divisor_for_minutes / 60);

          const divisor_for_seconds = divisor_for_minutes % 60;
          const seconds = Math.ceil(divisor_for_seconds);

          this.timeSpentText = `${minutes}:${seconds}`
        }
      }, 1000)
    },
    endGame() {
      this.gameActive = false
      this.timeSpentNum = 0
      this.timeSpentText = `00:00`
      this.$emit('setGameState', this.gameActive)
    }
  },
  created() {
    eventBus.$on("updatePairsFoundCount", () => {
      this.pairsFound++
      eventBus.$emit("pairCounterUpdated", this.pairsFound)
    }),
    eventBus.$on("updateMoveCounter", () => {
      this.moveCounter++
    })
    eventBus.$on("gameOver", () => {
      this.gameActive = false
    })
  }
}
</script>

<style>
</style>
