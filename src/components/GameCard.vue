<template>
  <div class="cursor-pointer" @click="flipCard">
    <div v-if="cardOpen">
        <section class="text-[#344054] font-500 text-[1rem] bg-none rounded-[0.5rem] w-[9rem] py-[6rem] border-[1px] border-[#D0D5DD] shadow-[0_1px_2px_rgba(16,24,40,0.05)] text-center">
            {{cardName}}
        </section>
    </div>
    <div v-if="!cardOpen">
        <section class="text-[#344054] font-500 text-[1rem] bg-none rounded-[0.5rem] w-[9rem] py-[6rem] border-[1px] border-[#D0D5DD] shadow-[0_1px_2px_rgba(16,24,40,0.05)] text-center">
            Card Back
        </section>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Controls',
    components: {},
    data() {
        return {
            cardOpen: false,
            pairFound: false,
            currentOpenCard: ""
        }
    },
    props: {
        id: {
            type: Number,
        },
        cardName: {
            type: String,
        }
    },
    methods: {
        flipCard() {
            this.cardOpen = !this.cardOpen
            if (this.cardOpen){
                this.currentOpenCard += this.cardName
                console.log(this.currentOpenCard)
            }
        }
    }
}
</script>

<style>
</style>
