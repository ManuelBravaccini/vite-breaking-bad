<script>
import { store } from '../store.js';
//import CardYuGiOh from './CardYuGiOh.vue';

export default {
    props: [
        'cards'
    ],

    data() {
        return {
            store,
        }
    },
}
</script>

<template>
    <main>
        <section class="container">
            <article v-for="cardEl in store.cardList">

                <img :src="cardEl.card_images.image_url" :alt="cardEl.name">

                <p v-for="cardEl in cards">
                    {{ cardEl.name }}
                </p>

            </article>
        </section>
    </main>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

main {
    background-color: $main-bg;
    //da togliere
    width: 100%;
    height: 2000px;
    //

    section.container {
        margin: 0 5rem;
        padding: 2rem;
        background-color: white;
    }
}
</style>