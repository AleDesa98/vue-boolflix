<template>
    <div v-if="ricerca.length == 0">
        Nessuna ricerca ancora effettuata
    </div>
    <div v-else>
        <section class="film-container" v-if="resultsFilm.length > 0">
            <h2>Film</h2>
            <ResultFilm
                v-for="resultFilm in resultsFilm"
                :key="resultFilm.id"
                :item="resultFilm"
            />
        </section>
        <section v-else>Film non trovati</section>

        <section class="serietv-container" v-if="resultsSerieTv.length > 0">
            <h2>Serie Tv</h2>
            <ResultSerieTv
                v-for="resultSerieTv in resultsSerieTv"
                :key="resultSerieTv.id"
                :item="resultSerieTv"
            />
        </section>
        <section v-else>Serie Tv non trovate</section>
        
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
    margin: 20px 0;
    h2 {
        width: 100%;
        text-align: center;
        margin: 20px;
    }
}
</style>