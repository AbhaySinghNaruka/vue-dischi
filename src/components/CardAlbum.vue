<template>
<div class="card">
  <div class="container-card">
    <img class="album-cover" :src="imageURL" alt="" />
    <div class="album-infos">
      <h2>{{ title }}</h2>
      <div class="artist">{{ artist }}</div>
      <div class="release-date">{{ releaseDate}} </div>
    </div>
  </div>

</div>
</template>

<script>
export default {
  props: {
    imageURL: String,
    title: String,
    artist: String,
    releaseDate: Number,

  },
};
</script>

<style lang="scss">
.card {
  width: 200px;
  background-color: #2E3A46;
  margin-bottom: 20px;

  .container-card {
    width: 80%;
    margin: 0 auto;
    padding: 25px 0;

    .album-cover {
      width: 100%
    }

    .album-infos {
      text-align: center;
      color: white;

      .artist {
        color: #546871;
      }

      .release-date {
        color: #546871;
      }
    }
  }
}
</style>
