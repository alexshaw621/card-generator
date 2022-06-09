<script>
import RandomCard from './RandomCard.vue';

export default {
  components: {
    RandomCard,
  },
  data() {
    return {
      formData: {
        count: { type: Number },
        dimension: { type: Number },
      },
      gridData: {
        count: 0,
        dimension: 0,
      },
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      this.gridData = { ...this.formData };
    },
  },
};
</script>

<template>
  <div class="container">
    <h1>Card Generator</h1>
    <form class="bg-white flex items-center" @submit="onSubmit">
      <div class="flex-1 flex items-center flex-col md:flex-row">
        <div class="flex items-center">
          <span>Genreate</span>
          <input type="number" max="5" v-model="formData.count" required />
          <span>random cards,</span>
        </div>
        <div class="flex items-center">
          <span>each with</span>
          <input type="number" max="5" v-model="formData.dimension" required />
          <span>rows/columns.</span>
        </div>
      </div>
      <div>
        <button class="button" type="submit">Genreate</button>
      </div>
    </form>

    <div>
      <div v-for="n in gridData.count" :key="n">
        <RandomCard :dimension="gridData.dimension" />
      </div>
    </div>
  </div>
</template>
