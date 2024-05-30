<script>

export default {
    props: {
        poster: String,
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String
    }
}
</script>

<template>

    <div class="movie">

        <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w342${poster}`" alt="poster" v-if="poster != null">
            <h3 v-else class="altPoster">{{ title }}</h3>
        </div>

        <div class="info">
            <strong>Titolo: </strong>{{ title }} <br>
            <strong>Titolo originale: </strong>{{ originalTitle }} <br>
            <strong>Voto: </strong><i class="fa-solid fa-star" v-for="element in Math.ceil(vote / 2)"></i><i
                class="fa-regular fa-star" v-for="element in (5 - Math.ceil(vote / 2))"></i> <br>
            <strong>Overview: </strong>{{ overview }}
        </div>
    </div>

</template>

<style scoped>
i {
    color: #FFBD01;
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>