<script>
export default {
  data() {
    return {
      perspective: 100,
      rotateX: 0,
      rotateY: 0,
      rotateZ: 0,
    };
  },
  computed: {
    box() {
      return {
        transform: `
          perspective(${this.perspective}px)
          rotateX(${this.rotateX}deg)
          rotateY(${this.rotateY}deg)
          rotateZ(${this.rotateZ}deg)
        `,
      };
    },
  },
  methods: {
    reset() {
        this.perspective = 100
        this.rotateX = 0
        this.rotateY = 0
        this.rotateZ = 0
    }
  }
};
</script>>

<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

const count = ref(0);
</script>

<template>
  <h2>CSS3 Perspective Playground</h2>
  <main>
    <section class="settings">
      <div class="settings-container">
        <label>perspective: {{ perspective }} px;</label>
        <input type="range" min="0" max="999" v-model="perspective" />

        <label>rotateX: {{ rotateX }} deg; </label>
        <input type="range" min="-180" max="180" v-model="rotateX" />

        <label>rotateY: {{ rotateY }} deg; </label>
        <input type="range" min="-180" max="180" v-model="rotateY" />

        <label>rotateZ: {{ rotateZ }} deg; </label>
        <input type="range" min="-180" max="180" v-model="rotateZ" />

        <button type="button" @click.prevent="reset">Reset</button>
        <button type="button">Copy</button>
      </div>
    </section>
    <section class="output">
      <div class="box-container">
        <div class="box" :style="box"></div>
      </div>
    </section>
  </main>
</template>

<style scoped>
h2 {
  color: #8d81f3;
  text-align: center;
  font-size: 40px;
  margin: 20px;
}

main {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 420px;
  max-width: 768px;
  margin: 0 auto;
  font-family: monospace, sans-serif;
  font-size: 22px;
  background-color: black;
}

main label {
  display: block;
}

main input[type="range"] {
  display: block;
  margin-bottom: 10px;
  width: 200px;
}

section.settings {
  width: 50%;
  z-index: 2;
}

.box-container {
  padding: 50px;
  border: 1px solid #8d81f3;
}

.box {
  width: 150px;
  height: 150px;
  background: #8d81f3;
}

button {
  background-color: #8d81f3;
  color: #fff;
  display: inline-block;
  font-size: 20px;
  padding: 10px;
  outline: none;
  border: none;
  margin-right: 10px;
}

label {
  color: #fff;
}
</style>
