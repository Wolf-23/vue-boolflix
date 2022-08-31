<template>
  <main>
        <div class="MyFilm">
            <div class="flip-card" v-for="(film, index) in listFilm" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.title">
                    </div>
                    <div class="flip-card-back">
                        <div><span>Titolo: </span>{{film.title}}</div>
                        <div><span>Titolo Originale: </span>{{film.original_title}}</div>
                        <div>
                            <span>Lingua: </span>
                            <img class="language" :src="getImage(film.original_language)" :alt="film.original_language">
                        </div>
                        <div v-if="getVote(film.vote_average) == 1">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(film.vote_average) == 2">
                            <span>Voto: </span>  
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(film.vote_average) == 3">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(film.vote_average) == 4">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else>
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="MySerie">
            <div class="flip-card" v-for="(serie, index) in listSerie" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" :alt="serie.name">
                    </div>
                    <div class="flip-card-back">
                        <div><span>Titolo: </span>{{serie.name}}</div>
                        <div><span>Titolo Originale: </span>{{serie.original_title}}</div>
                        <div>
                            <span>Lingua: </span>
                            <img class="language" :src="getImage(serie.original_language)" :alt="serie.original_language">
                        </div>
                        <div v-if="getVote(serie.vote_average) == 1">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(serie.vote_average) == 2">
                            <span>Voto: </span>  
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(serie.vote_average) == 3">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else-if="getVote(serie.vote_average) == 4">
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-regular fa-star"></i>
                        </div>
                        <div v-else>
                            <span>Voto: </span> 
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
  </main>
</template>
<!-- 
    Piena: <i class="fa-solid fa-star"></i>
    Vuota: <i class="fa-regular fa-star"></i>
 -->
<script>
    export default {
        name: 'MyMain',
        props: {
            listFilm: Array,
            listSerie: Array,
            visibility: Boolean

        },
        methods: {
            getImage(language) {
                let imageSrc = '';
                if(language == 'en' || language == 'it' || language == 'fr') {
                    imageSrc = require('../assets/flag/flag-of-' + language + '.png');
                } else {
                    imageSrc = language;
                }
                return imageSrc;
            },
            getVote(vote_average) {
                return Math.ceil(vote_average / 2);
            }
        },
    }
</script>

<style scoped lang="scss">
    @import '~@fortawesome/fontawesome-free/css/all.css';
    main {
        background-color: rgb(49, 49, 49);
    }
    .MyFilm, .MySerie {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        padding-top: 25px;
            .flip-card {
                background-color: transparent;
                width: calc(100% / 3 - 40px);
                height: 500px;
                margin: 20px;
                .flip-card-inner {
                    position: relative;
                    width: 100%;
                    height: 100%;
                    transition: transform 0.8s;
                    transform-style: preserve-3d;
                    .flip-card-front, .flip-card-back {
                        position: absolute;
                        width: 100%;
                        height: 100%;
                        -webkit-backface-visibility: hidden;
                        backface-visibility: hidden;
                    }
                    .flip-card-front {
                        color: black;
                        img {
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                            object-position: top;
                        }
                    }
                    .flip-card-back {
                        background-color: black;
                        color: white;
                        transform: rotateY(180deg);
                        padding: 25px;
                        .language {
                            width: 15px;
                        }
                    }
                }
                &:hover {
                .flip-card-inner { transform: rotateY(180deg);}
                }
            }
    }
</style>