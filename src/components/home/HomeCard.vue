<template lang="html">
  <div class="home-card card">
    <div class="card--container">
      <div class="card--title">
        <i v-bind:class="[icon]" class="icon icon-lg"></i>&nbsp;
        {{ title }}
      </div>
      <div class="card--content">
        {{ content }}
      </div>
      <div class="card--action">
        <button class="btn btn-primary">
          <span>Explore</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeCard",
  props: {
    icon: String,
    title: String,
    content: String
  }
};
</script>

<style lang="scss" scoped>
.home-card {
  margin: 10px;
  width: 20.5rem;
  box-sizing: border-box;
  .card--content {
    height: 4.5rem;
    max-height: 90px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}
</style>
