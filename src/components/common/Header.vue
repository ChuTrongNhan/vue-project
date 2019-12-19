<template lang="html">
  <div class="header-container">
    <div class="header-logo"></div>
    <div class="menu-container">
      <router-link
        v-bind:to="item.link"
        v-for="item in menuItems"
        v-bind:key="item.id"
        v-bind:class="[state == item.id ? 'menu-ul__active' : '', 'menu-ul']"
      >
        <span>{{ item.name }}</span>
        <i v-bind:class="['icon', 'icon-lg', item.icon]"></i>
      </router-link>
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
        {
          id: 1,
          name: "Home",
          icon: "ion-md-home",
          link: "/home"
        },
        {
          id: 2,
          name: "Pokedex",
          icon: "ion-ios-list",
          link: "/pokedex/lucario"
        },
        {
          id: 3,
          name: "Location",
          icon: "ion-md-locate",
          link: "#"
        },
        {
          id: 4,
          name: "Games",
          icon: "ion-logo-game-controller-b",
          link: "#"
        }
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
  .header-container {
    margin: 10px;
    border-radius: 45px;
    width: calc(100vw - 20px);
  }

  .menu-ul {
    margin: 0 calc(12.5% - 25px);
    border-radius: 30px;
    width: 50px;

    span {
      display: none;
    }

    i {
      display: unset;
    }
  }
}
</style>
