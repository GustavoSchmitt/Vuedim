<template>

    <h1 class="caramel"> {{ profile.title }}</h1>
    <img v-if="!!profile.img.length" :src="profile.img[0]" alt="">
    <Carousel :images="profile.img" />
    <section v-for="description in profile.description">
        <p>
            {{ description }}
        </p>

    </section>
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
img {
    border-radius: 45%;
    width: 150px;
}
section{
    display:flex;
    justify-content: center;
}
p{
    width:80%;
    font-size: 1.25rem;
}
</style>