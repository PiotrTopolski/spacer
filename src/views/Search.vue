<template>
  <div class="wrapper">
    <Claim></Claim>
    <SearchInput></SearchInput>
  </div>
</template>

<script>
import axios from "axios";
import debounce from "lodash.debounce";
import Claim from "../components/Claim";
import SearchInput from "../components/SearchInput";
const API = "https://images-api.nasa.gov/search";
export default {
  name: "Search",
  components: { Claim, SearchInput },
  data() {
    return {
      searchValue: "",
      results: []
    };
  },
  methods: {
    handleInput: debounce(function() {
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.results = response.data.collection.items;
        })
        .catch(error => {
          console.log(error);
        });
    }, 1000)
  }
};
</script>

<style scoped lang="scss">
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  min-height: 100vh;
  background-image: url(../assets/moon-2048727_1920.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
