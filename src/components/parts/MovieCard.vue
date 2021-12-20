<template>
  <div class="card">
    <h2>{{ infos.title }}</h2>
    <h3>{{ infos.original_title }}</h3>
    <span v-if="infos.original_language == ''">Lingua non disponibile</span>
    <img
      v-else
      :src="
        require('../../assets/img/flags/' + infos.original_language + '.png')
      "
      class="language"
    />
    <p class="Vote">{{ infos.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    infos: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
  padding: 15px 40px;
  .language {
    max-width: 30px;
  }
}
</style>