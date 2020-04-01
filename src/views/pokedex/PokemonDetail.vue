<template lang="html">
  <div class="home">
    <Header v-bind:state="2"></Header>
    <div v-if="!loading && !error" class="container">
      <InfoGeneral v-bind:pokemon="pokemon"></InfoGeneral>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/common/Header.vue";
import InfoGeneral from "@/components/pokedex/pokemon-detail/InfoGeneral.vue";

export default {
  name: "PokemonDetail",
  components: {
    Header,
    InfoGeneral
  },
  props: { name: String },
  data() {
    return {
      error: false,
      loading: true,
      pokemon: {
        infoGeneral: {}
      }
    };
  },
  created() {
    this.loading = true;
    this.error = false;
    this.getPokemonData1();
  },
  methods: {
    errorHandling() {
      // eslint-disable-next-line no-console
      console.log("Oopps! Somethings has gone wrong!");
    },

    sortBySlot(a, b) {
      return a.slot - b.slot;
    },

    getPokemonData2() {
      axios
        .get("https://pokeapi.co/api/v2/pokemon-species/" + this.name)
        .then(response => {
          if (response.status === 200) {
            Object.assign(this.pokemon.infoGeneral, {
              catchRate: response.data.capture_rate,
              genderRate: response.data.gender_rate,
              growthRate: response.data.growth_rate.name
            });
            response.data.genera.forEach(aGenera => {
              if (aGenera.language.name === "en")
                Object.assign(this.pokemon.infoGeneral, {
                  genera: aGenera.genus
                });
            });
          }
        })
        .catch(error => {
          this.errorHandling(error);
        })
        .finally(() => {
          this.loading = false;
        });
    },

    getPokemonData1() {
      axios
        .get("https://pokeapi.co/api/v2/pokemon/" + this.name)
        .then(response => {
          if (response.status === 200) {
            Object.assign(this.pokemon.infoGeneral, {
              id: response.data.id,
              name: response.data.name,
              abilities: response.data.abilities.sort(this.sortBySlot),
              types: response.data.types.sort(this.sortBySlot),
              stats: response.data.stats,
              imgURL: "https://img.pokemondb.net/artwork/" + this.name + ".jpg"
            });
            this.getPokemonData2();
          }
        })
        .catch(error => {
          this.errorHandling(error);
        });
    }
  }
};
</script>
