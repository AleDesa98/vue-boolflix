<template>
    <div>
        <Result
            v-for="(result, index) in results"
            :key="index"
            :item="result"
        />
    </div>
</template>

<script>
import Result from './Result.vue';
import axios from 'axios';

export default {
    name: 'Main',
    props: {
        ricerca: String
    },
    data: function() {
        return {
            results: []
        }
    },

    components: {
        Result
    },
    watch: {
        ricerca: function() {
            axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: '58063b74c8429ecd5c70268d5220db6a',
                    query: this.ricerca
                }
            })
            .then(
                res => {
                    this.results = res.data.results;
                }
            )
        }
    }
}
</script>

<style style lang="scss" scoped>
@import '../style/variables.scss';

div {
    display: flex;
    flex-wrap: wrap;
    margin: 20px 0;
}
</style>