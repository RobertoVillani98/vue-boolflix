<template>
  <div class="card">
    <h2>{{ infos.title }}</h2>
    <h3>{{ infos.original_title }}</h3>
    <p class="language">{{ infos.original_language }}</p>
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
}
</style>