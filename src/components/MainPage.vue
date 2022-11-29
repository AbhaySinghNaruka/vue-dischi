<template>
<main>
  <ListAlbum
  @generatedGenres="passaAlPadre"
  :arrivedGenre="selectedGenre"
  />
</main>
</template>

<script>
import ListAlbum from '@/components/ListAlbum.vue';

export default {
  components: {
    ListAlbum,
  },
  data() {
    return {

    };
  },
  props: {
    selectedGenre: String,
  },

  methods: {
    passaAlPadre(arr1) {
      this.$emit('generatedGenresSecond', arr1);
    },
  },
};
</script>

<style lang="scss">
main {
  height: calc(100vh - 100px);
  background-color: #1E2D3B;
}
</style>
