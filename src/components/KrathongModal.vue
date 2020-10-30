<template>
    <div class="selection">
        <div v-for="krathong in krathongList" :key="krathong.name" class="choice">
            <img :src="krathong.image">
            <p>{{krathong.name}}</p>
        </div>
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
}
</style>