<template>
    <div>
        <div class="left">
            <img src="../assets/img/logo.png" alt="">
        </div>
        <div class="right">
            <input type="text" placeholder="Search" v-model="inputText">
            <button type="submit" @click="$emit('search', inputText)">Cerca</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            inputText: ""
        }
    }
}
</script>

<style lang="scss" scoped>
    div {
        height: 60px;
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        input {
            margin-right: 10px;
            padding: 5px;
        }
        button {
            margin-right: 10px;
            padding: 5px;
            cursor: pointer;
        }
        img {
            height: 80%;
            margin-left: 10px;
        }
    }
</style>