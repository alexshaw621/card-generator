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
  <div class="container mx-auto">
    <h1 class="text-center md:text-left">Card Generator</h1>
    <form
      class="bg-white flex flex-col md:flex-row items-start md:items-center"
      @submit="onSubmit"
      data-generator-form
    >
      <div class="flex-1 flex items-center flex-col md:flex-row">
        <div class="flex items-center">
          <span>Genreate</span>
          <input type="number" min="1" v-model="formData.count" required />
          <span>random cards,&nbsp;</span>
        </div>
        <div class="flex items-center mt-3 md:mt-0">
          <span>each with</span>
          <input
            type="number"
            min="1"
            max="5"
            v-model="formData.dimension"
            required
          />
          <span>rows/columns.</span>
        </div>
      </div>
      <div class="w-full md:w-auto mt-3 md:mt-0">
        <button class="inline-block button w-full md:w-auto" type="submit">
          Genreate
        </button>
      </div>
    </form>

    <div class="flex flex-wrap justify-center mt-8">
      <div v-for="n in gridData.count" :key="n">
        <RandomCard :dimension="gridData.dimension" />
      </div>
    </div>
  </div>
</template>
