<script>
import axios from 'axios';

import { store } from "../store.js";

import AppSelect from "./AppSelect.vue";
import CardYuGiOh from './CardYuGiOh.vue';

export default {
    name: "AppMain",
    components: {
        CardYuGiOh,
        AppSelect,
    },

    data() {
        return {
            store,
            apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php",
        }
    },

    methods: {
        getCard() {
            axios.get(this.apiUrl, {
                params: {
                    num: 10,
                    offset: 0,
                },
            })
                .then((response) => {
                    //console.log(response.data.data);
                    this.store.cardList = response.data.data;
                    //console.log(store.cardList);
                })
                .catch(function (error) {
                    console.warn(error);
                });
        },
    },

    created() {
        this.getCard();
    },

}
</script>

<template>
    <main>
        <AppSelect />
        <section class="container">
            <CardYuGiOh v-for="(cardEl, index) in store.cardList" :key="index" :cardEl="cardEl" />
        </section>
    </main>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

main {
    background-color: $main-bg;
    height: 1250px;

    section.container {
        height: 1091px;
        overflow-y: auto;
        margin: 0 5rem;
        padding: 2rem;
        background-color: white;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
}
</style>