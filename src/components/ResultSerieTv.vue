<template>
    <div class="card-serietv">
        <img v-if="item.poster_path != null" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" alt="">
        <img v-else src="../assets/img/no-copertina.png" alt="">
        <div class="card-info">
            <h5>Titolo: <span>{{item.name}}</span></h5>
            <h6>Titolo originale: <span>{{item.original_name}}</span></h6>
            <h6>
                Lingua: 
                <span class="bandiera" v-if="item.original_language == 'en'"><img src="../assets/img/en.png" alt=""></span>
                <span class="bandiera" v-else-if="item.original_language == 'it'"><img src="../assets/img/it.png" alt=""></span>
                <span v-else> {{item.original_language}}</span>
            </h6>
            <h6>
                Voto: 
                <span>
                    <i class="fas fa-star"
                    v-for="index in stars" :key="index"
                    ></i>
                </span>
                <span>
                    <i  v-for="index in (5 - stars)" 
                        :key="index" 
                        class="far fa-star"></i>
                </span>
            </h6>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ResultSerieTv',
    data() {
        return {
            stars: Math.round(this.item.vote_average / 2)
        }
    },
    props: {
        item: Object
    }
}
</script>

<style style lang="scss" scoped>

.card-serietv {
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