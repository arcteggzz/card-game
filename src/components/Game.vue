<template>
    <section class="flex justify-center items-center h-[70vh]">
        <div
            class="grid grid-cols-8 gap-x-[2rem] gap-y-[2rem] py-[4rem]">
            <div v-for="(card, index) in cards" v-bind:key="index">
                <GameCard
                    v-bind:id ="card.id"
                    v-bind:cardName ="card.cardName"
                    v-bind:pairFound ="card.pairFound"
                    v-bind:cardOpen ="card.cardOpen"
                    v-bind:oneCardOpen="oneCardOpen"
                    @setIdState="setIdState"
                />
            </div>
        </div>
    </section>
</template>

<script>
import GameCard from "./GameCard.vue"
import { ref } from "vue"
import { eventBus } from "../main"

export default {
    name: 'Controls',
    components: { GameCard },
    data(){
        return {
            cards : ref([{
        id: 1,
        cardOpen: false,
        pairFound: false,
        cardName: "Messi",
    },
    {
        id: 2,
        cardOpen: false,
        pairFound: false,
        cardName: "Ronaldo",
    },
    {
        id: 3,
        cardOpen: false,
        pairFound: false,
        cardName: "Suarez",
    },
    {
        id: 4,
        cardOpen: false,
        pairFound: false,
        cardName: "Neymar",
    },
    {
        id: 5,
        cardOpen: false,
        pairFound: false,
        cardName: "Messi",
    },
    {
        id: 6,
        cardOpen: false,
        pairFound: false,
        cardName: "Ronaldo",
    },
    {
        id: 7,
        cardOpen: false,
        pairFound: false,
        cardName: "Suarez",
    },
    {
        id: 8,
        cardOpen: false,
        pairFound: false,
        cardName: "Neymar",
    },
    {
        id: 9,
        cardOpen: false,
        pairFound: false,
        cardName: "Messi",
    },
    {
        id: 10,
        cardOpen: false,
        pairFound: false,
        cardName: "Ronaldo",
    },
    {
        id: 11,
        cardOpen: false,
        pairFound: false,
        cardName: "Suarez",
    },
    {
        id: 12,
        cardOpen: false,
        pairFound: false,
        cardName: "Neymar",
    },
    {
        id: 13,
        cardOpen: false,
        pairFound: false,
        cardName: "Messi",
    },
    {
        id: 14,
        cardOpen: false,
        pairFound: false,
        cardName: "Ronaldo",
    },
    {
        id: 15,
        cardOpen: false,
        pairFound: false,
        cardName: "Suarez",
    },
    {
        id: 16,
        cardOpen: false,
        pairFound: false,
        cardName: "Neymar",
    },
    ]),
            cardA: "",
            cardAid: null,
            cardB: "",
            oneCardOpen: false,
            totalPairs: null,
            pairsFound: null
        }
    },
    created() {
        this.totalPairs = this.cards.length / 2
        eventBus.$on("pairCounterUpdated", (pairsFound) => {
            this.pairsFound = pairsFound
        })
    },
    methods: {
        setIdState(id){
            this.cards[id-1].cardOpen = true
            this.oneCardOpen = true
            //register you first card opened
            if (!this.cardA) {
                this.cardA = this.cards[id-1].cardName
                this.cardAid = id
            }
            //register your second card opened and incerement counter
            else {
                if (this.cardAid !== id) {
                    this.cardB = this.cards[id-1].cardName
                    eventBus.$emit('updateMoveCounter')
                }
            }
            console.log(this.cardA, this.cardB)
            //check if both cards are identical
            if (this.cardB){
                if (this.cardA === this.cardB){
                    console.log("1.update pairsFound count 2.make cards look red 3.reset all variables")
                    //1. update pairsFound using eventBus
                    eventBus.$emit('updatePairsFoundCount')
                    setTimeout(()=>{
                        //2. make cards look red by updating the original object array
                        this.cards[this.cardAid-1].pairFound = true
                        this.cards[id-1].pairFound = true
                        //3. reset all variables
                        this.cardA = ""
                        this.cardB = ""
                        this.cardAid = ""
                        if (this.totalPairs === this.pairsFound){
                            eventBus.$emit("gameOver")
                        }
                    }, 500)
                } else {
                    console.log("1. reset all variables 2. start a timer 3.close both open cards after timer runs out")
                    //2. start a timer
                    setTimeout(()=>{
                        //3. close both open cards
                        this.cards[id-1].cardOpen = false
                        this.cards[this.cardAid-1].cardOpen = false
                        this.oneCardOpen = false
                        //1.reset all variables
                        this.cardA = ""
                        this.cardB = ""
                        this.cardAid = ""
                    }, 1000)
                }
            }
        }
    }
}
</script>

<style>
</style>
