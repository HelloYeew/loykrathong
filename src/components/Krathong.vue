<template>
    <div class="krathong">
        <img class="krathong-image" :src="image" />
        <p class="krathong-text">
            {{ text }} 
        </p>
    </div>
</template>

<script>
export default {
    name: "Krathong",
    props: {
        text: {
            default: "",
            type: String
        },
        image:{
            default: "https://loremflickr.com/320/240",
            type: String
        }
    }
}
</script>

<style scoped>
.krathong {
    position: absolute;
    max-width: 320px;
    /* Please don't do this in production. */
    left: 200%;
    top: 50%;
    animation-name: float;
    animation-duration: 50s;
}

.krathong-image, .krathong-text {
    width: 100%;
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