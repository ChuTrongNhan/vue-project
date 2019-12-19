<template lang="html">
  <div class="home">
    <Header v-bind:state="2"></Header>
    dadssd {{ name }}
  </div>
</template>

<script>
import Header from "@/components/common/Header.vue";

export default {
  name: "PokemonDetail",
  components: {
    Header
  },
  props: { name: String }
};
</script>
