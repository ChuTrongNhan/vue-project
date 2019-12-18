<template lang="html">
  <div class="header-container">
    <div class="header-logo"></div>
    <div class="menu-container">
      <div
        v-for="item in menuItems"
        v-bind:key="item.id"
        v-bind:class="[state == item.id ? 'menu-ul__active' : '', 'menu-ul']"
      >
        <span>{{ item.name }}</span>
        <i v-bind:class="['icon', 'icon-lg', item.icon]"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    state: Number
  },
  data() {
    return {
      menuItems: [
        { id: 1, name: "Home", icon: "ion-md-home" },
        { id: 2, name: "Pokedex", icon: "ion-ios-list" },
        { id: 3, name: "Location", icon: "ion-md-locate" },
        { id: 4, name: "Games", icon: "ion-logo-game-controller-b" }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "./variables.scss";

.header-container {
  background-color: white;
  width: 100%;
  position: absolute;
  top: 0;
  height: $headerHeight;
  line-height: $headerHeight;
  box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.1);

  .menu-container {
    position: absolute;
    right: 0;
    top: 0;
    width: 500px;
    height: 100%;
    display: flex;
    flex-direction: row-reverse;

    .menu-ul {
      text-align: center;
      width: 25%;
      font-weight: $semibold;
      color: $gray;
      cursor: pointer;
    }

    .menu-ul__active {
      font-weight: $bold;
      color: $primaryColor;
    }

    .menu-ul:hover {
      background: $lightGray;
    }
  }
}

.menu-ul {
  span {
    display: unset;
  }

  i {
    display: none;
  }
}

@media (max-width: 1024px) {
  .menu-container {
    width: 100% !important;
    flex-direction: row !important;
  }
}

@media (max-width: 415px) {
  .menu-ul {
    span {
      display: none;
    }

    i {
      display: unset;
    }
  }
}
</style>
