<script>
export default {
  props: {
    color: Object,
    total: Number,
    index: Number,
  },
  data() {
    const { rgb, weight, hex } = this.color;
    return {
      bcg: rgb.join(","),
      hex: `#${hex}`,
      midIndex: Math.round(this.total / 2) - 1,
      alert: false
    };
  },
  methods: {
    coppyColor() {
      this.alert = true
      navigator.clipboard.writeText(this.hex);
     
      setTimeout(() => {
        this.alert = false
      }, 3000)
    },
  },
};
</script>
<template>
  <article class="color" @click="coppyColor" :class="{darkColor: index > midIndex, mainColor: index === midIndex}" :style="{backgroundColor: `rgb(${bcg})`}">
    <p>{{ color.weight }}%</p>
    <p>{{ hex }}</p>
    <p v-if="alert">Copied to clipboard</p>
  </article>
</template>
<style scoped>
.color {
  padding: 1rem 2rem;
  cursor: pointer;
  font-size: 1rem;
  text-transform: none;
}
.darkColor {
  color: #fff;
}
.mainColor {
  font-weight: bold;
  font-style: italic;
}
p {
  margin-bottom: 10px;
}
.button {
  background: #000;
  color: #fff;
  border-color: #000;
  transition: all 0.5s;
}
.button:hover {
  color: #000;
  background-color: #fff;
}
.button:focus {
  box-shadow: none
}
.form-control:focus, .form-select:focus {
  border-color: #5f9ea0;
  box-shadow: 0 0 0 0.25rem rgb(95 158 160 / 25%);
}
</style>
