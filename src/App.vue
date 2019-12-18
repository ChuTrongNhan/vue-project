<template>
  <div id="app">
    <div style="display: none" id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
@import "./components/common/styles.scss";
@import url("https://unpkg.com/ionicons@4.5.10-0/dist/css/ionicons.min.css");
</style>
