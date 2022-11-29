<template>
  <header>
    <div>
      <img class="logo" src="@/assets/img/logo.svg" alt="">
    </div>
    <button v-for="(genre, index) in generi" :key="index"
  @click="attivaFiltro(genre)"
  >{{ genre }}</button>
  <button @click="attivaFiltro('')">ALL</button>
  </header>
</template>

<script>
export default {
  props: {
    generi: Array,
  },
  methods: {
    attivaFiltro(nomeFiltro) {
      console.log(`Sto attivando il filtro: ${nomeFiltro}`);
      this.$emit('selectedFilter', nomeFiltro);
    },
  },
};
</script>

<style lang="scss">
  header {
    height: 100px;
    background-color: #2E3A46;
    display: flex;
    align-items:center;
  }

  .logo {
    height: 80px;
  }
</style>
