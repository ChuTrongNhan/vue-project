<template lang="html">
  <div class="general">
    <div class="general--upper">
      <img
        v-bind:src="pokemon.infoGeneral.imgURL"
        alt="No image loaded"
        height="255"
        width="255"
      />
      <div class="pkm--name">{{ pokemon.infoGeneral.name }}</div>
      <div class="pkm--species">{{ pokemon.infoGeneral.genera }}</div>
      <div class="pkm--types">
        <div
          v-for="type in pokemon.infoGeneral.types"
          v-bind:key="type.slot"
          class="pkm--types--tag"
        >
          {{ type.type.name }}
        </div>
      </div>
    </div>
    <div class="general--bottom">
      <div class="general--bottom--head">
        <span class="national-id">
          National No.{{ pokemon.infoGeneral.id }}
        </span>
      </div>
      <div class="general--bottom--body">
        <table cellspacing="0">
          <tr>
            <th>abilities</th>
            <td>
              <div
                v-for="ability in pokemon.infoGeneral.abilities"
                v-bind:key="ability.slot"
              >
                <span>{{ ability.ability.name.replace(/-/g, " ") }}</span>
                <span
                  v-if="ability.is_hidden"
                  class="hidden-ability"
                >
                  (hidden ability)
                </span>
              </div>
            </td>
          </tr>
          <tr>
            <th>catch rate</th>
            <td>{{ pokemon.infoGeneral.catchRate }}</td>
          </tr>
        </table>
      </div>
      <div class="general--bottom--foot">

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoGeneral",
  props: {
    pokemon: Object
  }
};
</script>

<style lang="scss" scoped>
@import "./InfoGeneral.scss";
</style>
