<template>
  <header>
    <div class="logo">
      <img src="../../assets/img/logo.png" alt="Boolflix logo" />
    </div>
    <div class="search">
      <input type="text" v-model="searchText" @keyup.enter="onSearchMovie()" />
      <button @click="onSearchMovie()">Cerca</button>
    </div>
  </header>
</template>

<script>
import axios from "axios";
import dataShared from "../../shared/dataShared.js";

export default {
  name: "Header",
  data() {
    return {
      dataShared,
      searchText: "",
    };
  },
  methods: {
    onSearchMovie: function () {
      if (this.searchText == "") {
        alert("Inserisci un valore corretto!");
      } else {
        axios
          .get("https://api.themoviedb.org/3/search/movie", {
            params: {
              api_key: "a5d4aefd1e1ce7fe4d2d5ca9a4b8ac1d",
              query: this.searchText,
              language: "it-IT",
            },
          })
          .then(function (response) {
            dataShared.searchResults = response.data.results;
          })
          .catch(function (error) {
            console.log(error);
          });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(13, 13, 13);
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 40px;
  .logo,
  .logo img {
    height: 100%;
  }
}
input {
  margin-right: 10px;
  border-radius: 10px;
  border: none;
  padding: 5px;
}
button {
  padding: 5px;
  border-radius: 10px;
  border: none;
  text-align: center;
  cursor: pointer;
}
</style>