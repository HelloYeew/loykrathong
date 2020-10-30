<template>
    <div class="selection">
        <button v-for="krathong in krathongList" :key="krathong.name" class="choice">
            <img :src="krathong.image">
            <p>{{krathong.name}}</p>
        </button>
    </div>
</template>
<script>
import krathongList from '../krathongList'
export default {
    name: "KrathongModal",
    data() {
        return {
            krathongList
        }
    }
}
</script>

<style scoped>
.selection {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    padding: 1rem;
    color: black;
}
.choice {
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.33rem;
    transition: all .4s ease-in-out;
}
.choice:hover, .choice:active {
    transform: scale(1.1);
}
</style>