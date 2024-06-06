<template>
    <main>
        <h1 class="caramel"> {{ profile.title }}</h1>
        <Carousel :images="profile.img" />
        <section>
            <p v-for="description in profile.description">
                {{ description }}

            </p>
        </section>
    </main>
</template>
<script>
import profiles from '../data/json.json'
import Carousel from '../components/Carousel.vue'
export default {
    name: 'profile',
    computed: {
        profile() {
            return profiles.find(profile => { return profile.id === parseInt(this.$route.params.id) })
        }
    },
    components: {
        Carousel,
    },
}
</script>
<style scoped>
main {
    background-color: var(--c-white);
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

img {
    border-radius: 45%;
    width: 150px;
}

section {
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 1rem;
}

p {
    width: 80%;
    font-size: 1.25rem;
}
</style>