<script>

export default {
    name: "Movies",
    props: {
        poster: String,
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String
    },
    methods: {
        overviewEllipsator() {
            if (this.overview.length > 380) {
                let i = 379;
                while(this.overview[i]!= " "){
                    i--;
                }
                return this.overview.slice(0, i) + "...";
            } else {
                return this.overview;
            }
        }
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

            <div class="title">
                <strong>Titolo: </strong>{{ title }}
            </div>

            <div class="original_title">
                <strong>Titolo originale: </strong>{{ originalTitle }}
            </div>

            <div class="rating">
                <strong>Voto: </strong><i class="fa-solid fa-star" v-for="element in Math.ceil(vote / 2)"></i><i
                    class="fa-regular fa-star" v-for="element in (5 - Math.ceil(vote / 2))"></i>
            </div>

            <div class="overview">
                <strong>Overview: </strong>{{ overviewEllipsator() }}
            </div>

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

.movie:hover .poster {
    opacity: 0;
}

.movie:hover .info {
    opacity: 1;
}
</style>