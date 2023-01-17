<script>
export default {
    name: "CardYuGiOh",
    props: {
        cardEl: Object,
    },
}
</script>

<template>
    <article class="single-character">
        <img :src="cardEl.card_images[0].image_url" :alt="cardEl.name">
        <div>
            <h5>{{ cardEl.name }}</h5>
            <p>
                {{ cardEl.archetype }}
            </p>
        </div>
    </article>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

article {
    margin: 1rem;
    font-size: 0.75rem;
    width: 200px;
    height: 400px;
    background-color: $main-bg;
    margin-bottom: 2rem;

    img {
        width: 100%;
    }

    div {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: .5rem;

        h5 {
            font-size: 1rem;
            color: white;
            margin-top: .5rem;
        }

        p {
            font-size: 1rem;
            margin-top: .5rem;
        }
    }


}
</style>