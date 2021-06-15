<template>
    <div class="card-film">
        <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" alt="">
        <div class="card-info">
            <h5>Titolo: <span>{{item.title}}</span></h5>
            <h6>Titolo originale: <span>{{item.original_title}}</span></h6>
            <h6>
                Lingua: 
                <span class="bandiera" v-if="item.original_language == 'en'"><img src="../assets/img/en.png" alt=""></span>
                <span class="bandiera" v-else-if="item.original_language == 'it'"><img src="../assets/img/it.png" alt=""></span>
                <span v-else> {{item.original_language}}</span>
            </h6>
            <h6>
                Voto: 
                <span v-if="Math.round(item.vote_average / 2) == 0"><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>
                <span v-else-if="Math.round(item.vote_average / 2) == 1"><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>
                <span v-else-if="Math.round(item.vote_average / 2) == 2"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>
                <span v-else-if="Math.round(item.vote_average / 2) == 3"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>
                <span v-else-if="Math.round(item.vote_average / 2) == 4"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i></span>
                <span v-else-if="Math.round(item.vote_average / 2) == 5"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></span>
            </h6>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ResultFilm',
    data() {
        return {
            
        }
    },
    props: {
        item: Object
    },
    methods: {
        
    }
}
</script>

<style style lang="scss" scoped>

.card-film {
    width: 150px;
    height: 220px;
    margin: 10px;
    position: relative;
    cursor: pointer;
    & > img {
        width: 100%;
        height: 100%;
    }
    &:hover .card-info {
        display: block;
    }
    .card-info {
        display: none;
        position: absolute;
        top: 0;
        width: 100%;
        height: 100%;
        padding: 15px;
        color: red;
        background-color: rgba(black, 0.8);

        & h6 {
            margin: 5px 0;
            font-size: 12px;
        }
        
        & h5 {
            font-size: 14px;
        }

        & span {
            color: white;
        }

    }
}
.bandiera > img {
    width: 20px;
}

</style>