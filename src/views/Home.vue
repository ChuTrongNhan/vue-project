<template>
  <div class="home">
    <Header v-bind:state="1"></Header>
    <div class="container">
      <HomeSearch />
      <div class="home-card--group">
        <HomeCard
          icon="ion-ios-list"
          title="Pokedex"
          content="Est adipisicing dolore adipisicing ut elit amet consequat veniam duis. Sint ore."
        />
        <HomeCard
          icon="ion-md-locate"
          title="Locations"
          content="Est adipisicing dolore adipisicing ut elit amet consequat veniam duis. Sint ea dolore."
        />
        <HomeCard
          icon="ion-logo-game-controller-b"
          title="Games"
          content="Est adipisicing dolore adipisicing ut elit amet consequat venia"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/common/Header.vue";
import HomeSearch from "@/components/home/HomeSearch.vue";
import HomeCard from "@/components/home/HomeCard.vue";

export default {
  name: "home",
  components: {
    Header,
    HomeCard,
    HomeSearch
  }
};
</script>

<style lang="scss" scoped>
.home-card--group {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
@media (max-width: 1024px) {
  .home-card--group {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 100px;
  }
}
</style>
