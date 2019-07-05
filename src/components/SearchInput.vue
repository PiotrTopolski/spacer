<template>
  <div class="searchWrapper">
    <input
      type="text"
      name="search"
      id="search"
      v-model="searchValue"
      @input="handleInput"
    />
  </div>
</template>

<script>
export default {
  name: "Searchinput"
};
</script>
<style scoped lang="scss">
.searchWrapper {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  width: 300px;
  input {
    height: 30px;
    border: 0;
    background-color: transparent;
    color: #fefefe;
    border-bottom: 1px solid;
  }
}
</style>
