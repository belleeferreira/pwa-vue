<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <CardPokemonSelected
        :name="pokemonSelected?.name"
        :xp="pokemonSelected?.base_experience"
        :height="pokemonSelected?.height"
        :image="pokemonSelected?.sprites.other.dream_world.front_default"
        :loading="loading"
        />

        <div class="col-sm-12 col-md-6">
          <div class="card cardList">
            <div class="card-body row">
              <div class="mb-3">
                <label hidden for="searchPokemonField" class="form-label"
                  >Pesqueisar</label
                >
                <input
                v-model="searchPokemonField"
                  type="text"
                  class="form-control"
                  id="searchPokemonField"
                  placeholder="Pesquisar..."
                />
              </div>
              <ListPokemons
                v-for="pokemon in pokemonsFiltered"
                :key="pokemon.name"
                :name="pokemon.name"
                :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
                @click="selectPokemon(pokemon)"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
   
  
  
<script setup>
import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "../components/ListPokemons.vue";
import CardPokemonSelected from "../components/CardPokemonSelected.vue"
let pokemons = reactive(ref());
let urlBaseSvg = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
);
let searchPokemonField = ref("")
let pokemonSelected = reactive(ref())
let loading = ref(false)

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then((res) => res.json())
    .then((res) => (pokemons.value = res.results));
});

const pokemonsFiltered = computed(() => {
  if(pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter(pokemon=> pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase()))
  }
  return pokemons.value
})

const selectPokemon = async (pokemon) => {
  loading.value = true;
  try {
    const response = await fetch(pokemon.url);
    if (!response.ok) {
      throw new Error('Failed to fetch Pokémon data');
    }
    const data = await response.json();
    pokemonSelected.value = data;
  } catch (error) {
    console.error(error);
    pokemonSelected.value = null;
    // Poderia exibir uma mensagem de erro ao usuário em vez de apenas logar no console
  } finally {
    loading.value = false;
  }
}
</script>

<style scoped>
.cardList{
  max-height: 74vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>