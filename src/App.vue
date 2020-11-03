<template>
  <div id="app">
    <h1>ลอยกระทง Simple </h1>
    <form @submit.prevent="submitKrathong" class="wish-form">
        <label class="label" for="wish">คำอธิษฐาน</label>
        <textarea rows="4" cols="30" class="input" v-model="wish" name="wish"/>
        <button class="form-button" @click.prevent="$modal.show('selection-modal')">เลือกกระทง</button>
        <span>{{ krathongName }}</span>
        <input :disabled="disabled" type="submit" class="form-button" value="ลอยกระทง"/>
    </form>
    <div class="pool">
      <krathong v-for="krathong in krathongQueue" :image="krathong.image" :text="krathong.wish" :key="krathong.time" />
    </div>
    <modal name="selection-modal" width="50%">
      <krathong-modal :krathongList="krathongList" :handleSelect="handleSelect"/>
    </modal>
  </div>
</template>

<script>
import Krathong from './components/Krathong.vue';
import KrathongModal from './components/KrathongModal.vue';
import krathongList from './krathongList';
export default {
  name: 'App',
  components: {
    Krathong,
    KrathongModal
  },
  data() {
    return {
      wish: "",
      krathongQueue: [],
      disabled: false,
      image: "",
      krathongList,
      krathongName: ""
    }
  },
  computed: {
    imageUrl() {
      return this.image == "" ? undefined : this.image;
    }
  },
  methods: {
    submitKrathong() {
      this.krathongQueue.push({
        wish: this.wish,
        time: (new Date()).getTime(),
        image: this.imageUrl,
      })
      this.disabled = true
      setTimeout(() => {
        this.disabled = false
      }, 500)
      setTimeout(() => {
        this.krathongQueue.unshift()
      }, 10000)
    },
    handleSelect(krathong) {
      this.image = krathong.image
      this.krathongName = krathong.name
      this.$modal.hide('selection-modal')
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
  overflow-x: hidden;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:aliceblue;
  padding: 1rem;
  height: 100%;
}
.form-button {
  display: block;
  margin: auto;
  margin-top: 1rem;
  background:#02326E;
  color: white;
  font-weight: bold;
  border: 1px solid rgba(255, 255 ,255, 0.33);
  padding: .33rem;
  cursor: pointer;
}
.form-button:active, .form-button:hover {
  background: #CAE00F;
  color: rgb(44, 44, 44);
}
.form-button:disabled {
  color: gray;
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
