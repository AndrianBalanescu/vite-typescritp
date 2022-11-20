<template>
  <div class="hello mx-10">
    <h1>{{ msg }}</h1>

    <h5
      class="b-3 b-dashed b-red"
      :style="{
        color: color,
        backgroundColor: this.pickRandomItemFromArray(this.colors),
        borderRadius: '10px',
      }"
    >
      Count: {{ count }}
      {{ color }}
    </h5>
    <section class="my-1">
      <div v-for="(color, index) in colors" :key="index">
        <!-- {{ color }} -->
        <div
          class="my-12"
          :style="{
            backgroundColor: color,
          }"
        >
          {{ color }}
        </div>
      </div>
    </section>
    <!-- {{ this.pickRandomItemFromArray(this.colors) }}
    {{ this.pickRandomItemFromArray(this.colors) }} -->
    <button type="submit" @click="countMethod(1)">Add:1</button>

    <button type="submit" @click="countMethod(5)">Add:5</button>
    <button type="submit" @click="addAtInterval()">Auto</button>
    <div v-if="count > 15">
      <h5>Ooops you are about to be maxed out!!!</h5>
    </div>
    {{ count }}
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      count: 0,
      showMessage: false,
      color: "red",
      colors: ["blue", "lime", "green", "yellow", "cyan"],
      // color: red,
    };
  },
  methods: {
    countMethod(number) {
      this.count += number;
    },
    addAtInterval() {
      setInterval(() => {
        this.count = this.count + 1;
      }, 1000);
    },
    pickRandomItemFromArray(array) {
      return array[Math.floor(Math.random() * array.length)];
    },
  },
  watch: {
    count(val) {
      console.log(val);
      if (val > 21) {
        this.count = 0;
      }
      this.color = this.pickRandomItemFromArray(this.colors);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h5 {
  font-size: 25px;
  color: blue;
}
button {
  padding: 10px;
  background-color: lime;
  margin: 10px;
  border-radius: 10%;
  box-shadow: 1px 1px 1px blue;
  min-width: 75px;
}
button:hover {
  padding: 10px;
  background-color: lime;
  opacity: 0.8;
  margin: 10px;
  border-radius: 10%;
  box-shadow: 1px 1px 1px blue;
  min-width: 75px;
  border: 1px dashed white;
  scale: 1.05;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
