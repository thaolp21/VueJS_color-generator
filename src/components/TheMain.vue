<script>
import Values from "values.js";
import SingleColor from "./SingleColor.vue";

export default {
  data() {
    const initColors = new Values("#f15025").all(10);
    return {
      color: "",
      error: "",
      weight: 10,
      listColors: initColors,
      componentKey: 0,
    };
  },
  methods: {
    handleSubmit() {
      const _weight = this.weight * 1;
      try {
        let colors = new Values(this.color).all(_weight);
        this.listColors = colors;
        this.error = false;
        this.componentKey += 1;
      } catch (e) {
        this.listColors = [];
        this.error = true;
        this.componentKey = 0;
      }
    },
  },
  components: { SingleColor },
};
</script>
<template>
  <section>
    <form @submit.prevent="handleSubmit" class="form">
      <input
        type="text"
        v-model="color"
        placeholder="#f15025"
        class="selectForm"
      />
      <select v-model="weight" class="selectForm">
        <option value="default">Choose the weight (default 10)</option>
        <option value="1">1</option>
        <option value="5">5</option>
        <option value="10">10</option>
        <option value="20">20</option>
        <option value="50">50</option>
      </select>
      <button class="btnForm">Submit</button>
    </form>
    <p v-if="error">Please type hexadecimal RGB value: #RGB #RRGGBB</p>
  </section>
  <section class="colors" :key="componentKey">
    <SingleColor
      v-for="(item, index) in listColors"
      :color="item"
      :index="index"
      :total="listColors.length"
      :key="index"
    />
  </section>
</template>
<style scoped>
.sectionBody {
  display: flex;
  flex-wrap: wrap;
}
.form {
  /* text-align: center; */
  margin: 10px 0;
  display: flex;
  place-items: center;
}
.btnForm {
  background-color: #fff;
  font-weight: 400;
  line-height: 1.5;
  border-radius: 5px;
  cursor: pointer;
  color: #f15025;
  border: 2px #F15025 solid;
}
.selectForm {
  display: block;
  width: 100%;
  padding: 0.375rem 2.25rem 0.375rem 0.75rem;
  margin: 0 10px;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  border: 1px #000 solid;
  border-radius: 5px;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
.colors {
  min-height: calc(100vh - 100px);
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(223.33px, 1fr));
  grid-template-rows: repeat(auto-fit, minmax(96px, 1fr));
}
</style>
