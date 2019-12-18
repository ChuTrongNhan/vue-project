<template lang="html">
  <div class="home-search">
    <div class="home-search--input">
      <input
        v-model="searchPokemon"
        spellcheck="false"
        placeholder="Which pokemon are you looking for?"
      />
    </div>
    <div class="home-search--button">
      <button type="button" class="btn btn-outline">
        <i class="icon icon-md ion-ios-search"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeSearch"
};
</script>

<style lang="scss" scoped>
.home-search {
  display: flex;
  flex-direction: column;
  padding: 50px 0;
  div {
    margin-bottom: 15px;
  }
}

.home-search--input,
.home-search--button {
  margin: auto;
}

.home-search--input input {
  width: 24.5rem;
}

.home-search--button button {
  width: 90px;
  transition: 0.3s ease-in-out;
}

.home-search--button button:hover {
  width: 24rem;
  border-radius: 0;
}
</style>
