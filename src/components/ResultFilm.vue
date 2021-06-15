<template>
    <div>
        <ul>
            <li>{{item.title}}</li>
            <li>{{item.original_title}}</li>
            <li v-if="item.original_language == 'en'"><img src="../assets/img/en.png" alt=""></li>
            <li v-else-if="item.original_language == 'it'"><img src="../assets/img/it.png" alt=""></li>
            <li v-else> {{item.original_language}}</li>
            <li>{{Math.round(item.vote_average / 2)}}</li>
            <li v-if="Math.round(item.vote_average / 2) == 0"><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></li>
            <li v-else-if="Math.round(item.vote_average / 2) == 1"><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></li>
            <li v-else-if="Math.round(item.vote_average / 2) == 2"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></li>
            <li v-else-if="Math.round(item.vote_average / 2) == 3"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></li>
            <li v-else-if="Math.round(item.vote_average / 2) == 4"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i></li>
            <li v-else-if="Math.round(item.vote_average / 2) == 5"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></li>
        </ul>
        <img class="copertina" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" alt="">
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
div {
    width: calc(100% / 5);
    ul {
        list-style: none;
        li {
            img {
                height: 10px;
            }
        }
    }
}
.copertina {
    height: 100px;
}
</style>