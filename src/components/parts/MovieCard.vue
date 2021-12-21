<template>
  <div class="card">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + infos.poster_path"
      :alt="'Poster ' + infos.id"
    />
    <h2 v-if="type == 'movie'">{{ infos.title }}</h2>
    <h2 v-else>{{ infos.name }}</h2>
    <h3 v-if="type == 'movie'">{{ infos.original_title }}</h3>
    <h3 v-else>{{ infos.original_name }}</h3>
    <div class="votes">
      <span v-if="infos.original_language == ''">Lingua non disponibile</span>
      <img
        v-else
        :src="
          require('../../assets/img/flags/' + infos.original_language + '.png')
        "
        class="language"
      />
      <span class="Vote" v-for="index in stars" :key="index"
        ><i class="fas fa-star"></i
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    infos: Object,
    type: String,
  },
  data() {
    return {
      stars: Math.ceil(this.infos.vote_average / 2),
    };
  },
};
</script>

<style lang="scss" scoped>
.card {
  padding: 15px 40px;
  .language {
    max-width: 30px;
    margin-right: 10px;
  }
  .votes {
    display: flex;
    align-items: center;
  }
  .Vote {
    color: rgb(219, 219, 0);
  }
}
</style>