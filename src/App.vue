<template>
  <input v-model.number="k" placeholder="edit me" />

  <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
    <g>
      <circle cx="50" cy="50" r="10" />
    </g>
    <g fill="white">
      <circle cx="50" cy="50" r="9.7" />
    </g>
    <g
      v-for="i in range(k)"
      key="i"
      fill="blue"
      :transform="`rotate(${angle_generator[i]} 50 50) translate(0 10)`"
    >
      <circle cx="50" cy="50" r="1" />
      <text
        x="50"
        y="50"
        fill="red"
        font-size="20%"
        :transform="`rotate(${angle_alignment[i]} 50 50) translate(-1, -10) `"
      >
        {{ id_generator[i] }}
      </text>
    </g>
  </svg>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      i: '',
      k: 1,
    };
  },
  methods: {
    range(k) {
      let result = Array(k);
      for (let i = 0; i < k; i++) {
        result[i] = i;
      }
      return result;
    },
  },
  computed: {
    angle_generator() {
      let n = 1;
      let nbr_angle_base = 360 / this.k;
      let nbr_angle = 360 / this.k;
      let angles = [180];

      while (n < this.k) {
        angles.push(180 + nbr_angle);
        nbr_angle += nbr_angle_base;
        n++;
      }

      return angles;
    },
    angle_alignment() {
      let n = 1;
      let nbr_angle_base = 360 / this.k;
      let nbr_angle = 360 / this.k;
      let angles = [180];

      while (n < this.k) {
        angles.push(180 - nbr_angle);
        nbr_angle += nbr_angle_base;
        n++;
      }

      return angles;
    },
    id_generator() {
      let id = [0];
      let n = 1;

      while (n < this.k) {
        id.push(n);
        n++;
      }
      return id;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#a {
  transform-origin: 50% 50%;
}

</style>
