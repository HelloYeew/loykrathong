<template>
    <div class="selection">
        <button @click="handleSelect(krathong)" v-for="krathong in krathongList" :key="krathong.name" class="choice">
            <img class="choice-image" :src="krathong.image">
            <p>{{krathong.name}}</p>
        </button>
    </div>
</template>
<script>
export default {
    name: "KrathongModal",
    props: {
        handleSelect: Function,
        krathongList: Array,
    },
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
.choice-image {
    width: 100%;
    height: auto;
}
</style>