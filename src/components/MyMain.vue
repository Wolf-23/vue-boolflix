<template>
  <main>
    <!-- Film -->
        <h3 class="searchTitle" v-if="visibilityFilm == true" >Film Ricercati:</h3>
        <div class="emptyArray" v-if="listFilm.length == [] && visibilityFilm == true">Nessun Risultato trovato!</div>
        <div class="MyFilm">
            <div class="flip-card" v-for="(film, index) in listFilm" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.title">
                    </div>
                    <div class="flip-card-back">
                        <div><span>Titolo: </span>{{film.title}}</div>
                        <div :class="(film.title == film.original_title || film.original_title == ''?'noShow': '')"><span>Titolo Originale: </span>{{film.original_title}}</div>
                        <div>
                            <span>Lingua: </span>
                            <img class="language" :src="getImage(film.original_language)" :alt="film.original_language">
                        </div>
                        <div :class="(film.overview == ''?'noShow':'')"><span>Trama: </span>{{film.overview}}</div> 
                        <div>
                            <i v-for="n in 5" class="fa-star" :class="(n>=getVote(film.vote_average)?'fa-regular': 'fa-solid')" :key="n"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    <!-- Serie Tv --> 
        <h3 class="searchTitle" v-if="visibilitySerie == true">Serie TV Ricercate:</h3>
        <div class="emptyArray" v-if="listFilm.length == [] &&  visibilitySerie == true">Nessun Risultato trovato!</div>
        <div class="MySerie">
            <div class="flip-card" v-for="(serie, index) in listSerie" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" :alt="serie.name">
                    </div>
                    <div class="flip-card-back">
                        <div><span>Titolo: </span>{{serie.name}}</div>
                        <div :class="(serie.name == serie.original_name || serie.original_name == ''?'noShow': '')"><span>Titolo Originale: </span>{{serie.original_name}}</div>
                        <div>
                            <span>Lingua: </span>
                            <img class="language" :src="getImage(serie.original_language)" :alt="serie.original_language">
                        </div>
                        <div>
                            <i v-for="n in 5" class="fa-star" :class="(n>=getVote(serie.vote_average)?'fa-regular': 'fa-solid')" :key="n"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
  </main>
</template>
<script>
    export default {
        name: 'MyMain',
        props: {
            listFilm: Array,
            listSerie: Array,
            visibilityFilm: Boolean,
            visibilitySerie: Boolean

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
        .searchTitle {
            padding: 30px 0 10px;
            font-size: 30px;
        }
        .emptyArray, .searchTitle {
            color: white;
            text-align: center;
        }
        .emptyArray {
            padding-top: 20px;
        }
        .MyFilm, .MySerie {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
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
                            .noShow {
                                display: none;
                            }
                        }
                    }
                    &:hover {
                    .flip-card-inner { transform: rotateY(180deg);}
                    }
                }
        }
    }
</style>