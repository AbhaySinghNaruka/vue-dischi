<template>
  <div class="container">
    <CardAlbum
    v-for="(singleAlbum, index) in arrAlbumsFiltered" :key="index"
    :imageURL="singleAlbum.poster"
    :title="singleAlbum.title"
    :artist="singleAlbum.author"
    :releaseDate="singleAlbum.year"
    />
  </div>
</template>

<script>
import axios from 'axios';
import CardAlbum from './CardAlbum.vue';

export default {
  CardAlbum,
  components: { CardAlbum },
  props: {
    arrivedGenre: String,
  },
  methods: {
    generateGenres(arr) {
      const arrGenresInner = [];
      arr.forEach((album) => {
        if (arrGenresInner.indexOf(album.genre) === -1) {
          arrGenresInner.push(album.genre);
        }
      });
      return arrGenresInner;
    },
  },
  data() {
    return {
      arrAlbums: [],
      urlAPI: 'https://flynn.boolean.careers/exercises/api/array/music',
      arrGenres: [],
    };
  },
  mounted() {
    axios.get(this.urlAPI)
      .then((axiosResponse) => {
        this.arrAlbums = axiosResponse.data.response;
        this.arrGenres = this.generateGenres(this.arrAlbums); // ROCK,POP, JAZZ
        this.$emit('generatedGenres', this.arrGenres);
        console.log(this.arrAlbums);
      });
    console.log('created');
  },

  computed: {
    arrAlbumsFiltered() {
      if (this.arrAlbums) {
        if (this.arrivedGenre === '' || this.arrivedGenre === 'ALL') {
          return this.arrAlbums;
        }
        const filterArray = this.arrAlbums.filter(
          (album) => album.genre === this.arrivedGenre,
        );

        /* const filterInnerArray = [];

      this.arrAlbums.forEach((album) => {
        if (album.genre === this.arrivedGenre) {
          filterInnerArray.push(album);
        }
      }); */

        return filterArray;
      }

      return [];
    },
  },

};
</script>

<style lang="scss">
.container {
  width: 1200px;
  margin: 0 auto;
  height: 100%;
  padding: 100px 0;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 5px;
}
</style>
