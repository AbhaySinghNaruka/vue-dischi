<template>
  <div>
    <HeaderPage
    :generi="arrGenres"
    @selectedFilter="selezionaFiltro"
    />
    <MainPage
    @generatedGenresSecond="settingGenres"
    :selectedGenre="selectedGenreApp"
    />
  </div>
</template>

<script>
import HeaderPage from '@/components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      arrGenres: [],
      selectedGenreApp: '',
    };
  },
  methods: {
    settingGenres(arr2) {
      this.arrGenres = arr2;
    },
    selezionaFiltro(filtro) {
      this.selectedGenreApp = filtro;
      console.log(`Evento emesso e il filtro è: ${filtro}`);
    },
  },
};
</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
</style>
