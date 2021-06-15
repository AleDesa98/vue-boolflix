<template>
    <div class="no-ricerca" v-if="ricerca.length == 0">
        <p>Nessuna ricerca ancora effettuata</p>
    </div>
    <div class="ricerca" v-else>
        <section class="film-container" v-if="resultsFilm.length > 0">
            <h2>Film</h2>
            <ResultFilm
                v-for="resultFilm in resultsFilm"
                :key="resultFilm.id"
                :item="resultFilm"
            />
        </section>
        <section class="no-risultati" v-else>
            <p>Nessun film trovato</p>
        </section>

        <section class="serietv-container" v-if="resultsSerieTv.length > 0">
            <h2>Serie Tv</h2>
            <ResultSerieTv
                v-for="resultSerieTv in resultsSerieTv"
                :key="resultSerieTv.id"
                :item="resultSerieTv"
            />
        </section>
        <section class="no-risultati" v-else>
            <p>Nessuna serie tv trovata</p>
        </section>
        
    </div>
</template>

<script>
import ResultFilm from './ResultFilm.vue';
import ResultSerieTv from './ResultSerieTv.vue';
import axios from 'axios';

export default {
    name: 'Main',
    props: {
        ricerca: String
    },
    data: function() {
        return {
            resultsFilm: [],
            resultsSerieTv: []
        }
    },

    components: {
        ResultFilm,
        ResultSerieTv
    },
    watch: {
        ricerca: function() {
            axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: '58063b74c8429ecd5c70268d5220db6a',
                    language: "it_IT",
                    query: this.ricerca
                }
            })
            .then(
                res => {
                    this.resultsFilm = res.data.results;
                }
            )

            axios
            .get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: '58063b74c8429ecd5c70268d5220db6a',
                    language: "it_IT",
                    query: this.ricerca
                }
            })
            .then(
                res => {
                    this.resultsSerieTv = res.data.results;
                }
            )
        }
    }
}
</script>

<style style lang="scss" scoped>
@import '../style/variables.scss';

section {
    display: flex;
    flex-wrap: wrap;
    padding: 20px 0;
    h2 {
        width: 100%;
        text-align: center;
        margin: 20px;
        font-size: 35px;
        text-transform: uppercase;
    }
}



.no-ricerca {
    width: 100vw;
    height: calc(100vh - 60px);
    background-color: grey;
    position: relative;
}

.no-ricerca > p {
    position: absolute;
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 30px;
    text-align: center;
}

.ricerca {
    background-color: grey;
    height: 100%;
    min-height: calc(100vh - 60px);
}

.no-risultati {
    justify-content: center;
    & > p {
        text-transform: uppercase;
        font-size: 30px;
        font-weight: 700;
    }
}

.film-container,
.serietv-container {
    justify-content: center;
}
</style>