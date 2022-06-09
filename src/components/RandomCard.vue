<script>
export default {
  props: {
    dimension: { type: Number, default: 5 },
  },
  data() {
    return {
      availableLetters: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
      backupClasses:
        'grid-cols-1 grid-cols-2 grid-cols-3 grid-cols-4 grid-cols-5',
    };
  },
  computed: {
    totalCount() {
      return Math.pow(this.dimension, 2);
    },
    className() {
      return `inline-grid gap-3 grid-cols-${this.dimension}`;
    },
    shuffledLetters() {
      let letters = this.availableLetters.split('');
      const length = letters.length;

      for (let i = length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        const temp = letters[i];
        letters[i] = letters[j];
        letters[j] = temp;
      }

      return letters.slice(0, this.totalCount);
    },
  },
  methods: {},
};
</script>

<template>
  <div :class="className" :data-dimension="dimension" data-card>
    <span v-for="letter in shuffledLetters" :key="letter" data-card-letter>
      {{ letter }}
    </span>
  </div>
</template>
