<template>
    <div>
        <ul>
            <li>{{item.title}}</li>
            <li>{{item.original_title}}</li>
            <li v-if="item.original_language == 'en'"><img src="../assets/img/en.png" alt=""></li>
            <li v-else-if="item.original_language == 'it'"><img src="../assets/img/it.png" alt=""></li>
            <li v-else> {{item.original_language}}</li>
            <li>{{item.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Result',
    props: {
        item: Object
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
</style>