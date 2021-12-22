
<template>
  <div class="card">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + infos.poster_path"
      :alt="'Poster ' + infos.id"
    />

    <div class="text">
      <h2 v-if="type == 'movie'">{{ infos.title }}</h2>
      <h2 v-else>{{ infos.name }}</h2>
      <h3 v-if="type == 'movie'">{{ infos.original_title }}</h3>
      <h3 v-else>{{ infos.original_name }}</h3>
      <div class="votes">
        <span v-if="infos.original_language == ''">Lingua non disponibile</span>
        <img
          v-else
          :src="
            require('../../assets/img/flags/' +
              infos.original_language +
              '.png')
          "
          class="language"
        />
        <span class="Vote" v-for="index in stars" :key="index"
          ><i class="fas fa-star"></i
        ></span>
      </div>
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
  width: calc(100% / 4 - 80px);
  text-align: center;
  margin: 20px 20px;
  position: relative;
  border-radius: 20px;
  border: 1px solid white;
  cursor: pointer;

  &:hover > .text {
    opacity: 1;
  }

  .text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    overflow-y: auto;
    width: 340px;
    opacity: 0;
  }

  .language {
    max-width: 30px;
    margin-right: 10px;
  }

  .votes {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .Vote {
    color: rgb(219, 219, 0);
  }

  img {
    border-radius: 20px;
    width: 100%;
  }

  img:hover {
    opacity: 0.1;
  }
}
</style>