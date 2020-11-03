<template>
    <div class="krathong">
        <img class="krathong-image" :src="image" />
        <p class="krathong-text">
            {{ text }} 
        </p>
    </div>
</template>

<script>
import krathongList from '../krathongList';
export default {
    name: "Krathong",
    props: {
        text: {
            default: "",
            type: String
        },
        image:{
            default: krathongList[0].image,
            type: String
        }
    }
}
</script>

<style scoped>
.krathong {
    position: absolute;
    width: 320px;
    /* Please don't do this in production. */
    left: 200%;
    top: 50%;
    animation-name: float;
    animation-duration: 50s;
}

.krathong-image, .krathong-text {
    width: 100%;
    height: auto;
}

@keyframes float {
    0% {
        left: 100%;
    }
    100% {
        left: -200%;
    }
}
</style>