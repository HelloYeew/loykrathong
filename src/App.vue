<template>
  <div id="app">
    <h1>ลอยกระทง Simple </h1>
    <form class="wish-form">
        <label class="label" for="wish">คำอธิฐาน</label>
        <input class="input" v-model="wish" name="wish"/>
      <input type="submit" class="submit-button" value="ลอยกระทง"/>
    </form>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      wish: "",
      krathongQueue: [],
    }
  }
}
</script>

<style>
body {
  background: #141852; /* This is from https://www.schemecolor.com/night-sky-color-palette.php */
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
}
</style>
