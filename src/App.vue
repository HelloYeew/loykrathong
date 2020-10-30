<template>
  <div id="app">
    <h1>ลอยกระทง Simple </h1>
    <form @submit.prevent="submitKrathong" class="wish-form">
        <label class="label" for="wish">คำอธิฐาน</label>
        <textarea class="input" v-model="wish" name="wish"/>
      <input type="submit" class="submit-button" value="ลอยกระทง"/>
    </form>
    <div class="pool">
      <krathong v-for="krathong in krathongQueue" :text="krathong.wish" :key="krathong.time" />
    </div>
  </div>
</template>

<script>
import Krathong from './components/Krathong.vue';
export default {
  name: 'App',
  components: {
    Krathong
  },
  data() {
    return {
      wish: "",
      krathongQueue: [],
    }
  },
  methods: {
    submitKrathong() {
      this.krathongQueue.push({
        wish: this.wish,
        time: (new Date()).getTime()
      })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Athiti:wght@400;600&display=swap');
html, body {
  font-family: "Athiti", sans-serif;
}
body {
  background: #141852; /* This is from https://www.schemecolor.com/night-sky-color-palette.php */
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:aliceblue;
  padding: 1rem;
  height: 100%;
}
.submit-button {
  display: block;
  margin: auto;
  margin-top: 1rem;
  background: white;
  color: black;
  border: 1px solid aliceblue;
  padding: .33rem;
}
.wish-form {
  width: 80%;
  margin:auto;
  display: flex;
  flex-flow: column;
  align-items: center;
}
.input {
  margin-top: 1rem;
  width: 50ch;
}
</style>
