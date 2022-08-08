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

export default {
    name: 'Controls',
    components: { GameCard },
    data(){
        return {
            cards : [{
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
    ],
            cardA: "",
            cardB: "",
            oneCardOpen: false
        }
    },
    methods: {
        setIdState(id){
            console.log(id)
            this.cards.map((card) => {
                if (card.id === id) {
                    console.log("fired");
                    return {
                        ...card, cardOpen: true
                    }
                }
                return card
            })
        }
    }

}
</script>

<style>
</style>
