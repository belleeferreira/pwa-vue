<template>
    <div class="col-sm-12 col-md-6">
          <div class="card cardListPokemon"
            :class=" loading ? '' : 'animate__animated animate__flipInX'">
            <img
            v-if="pokemon.name"
              :src="pokemon.image"
              height="250"
              class="card-img-top pt-2"
              :alt="pokemon.name"
            />
            <img
            v-else
              src="../assets/egg_pokemon.svg"
              height="250"
              class="card-img-top pt-2"
              alt="???"
            />
            <div class="card-body">
              <h5 class="card-title text-center text-white">{{pokemon.name || '???'}}</h5>
              <hr>
                <div class="row">
                    <section class="col">
                        <strong>XP:</strong>
                        <span>{{ pokemon.xp }}</span>
                    </section>
                    <section class="col">
                        <strong>Altura:</strong>
                        <span>{{ pokemon.height }}</span>
                    </section>
                </div>
            </div>
          </div>
        </div>
</template>

<script setup>
    const pokemon =  defineProps (["name", "xp", "height", "image", "loading"])
</script>
<style scoped>
.cardListPokemon{
    height: 74vh;
    background: rgb(0,14,102);
    background: linear-gradient(90deg, rgba(0,14,102,1) 0%, rgba(82,0,120,0.6362920168067228) 0%, rgba(55,0,94,0.6418942577030813) 100%, rgba(95,147,255,0.4009978991596639) 100%);
}
strong, span{
    color: white;
    padding: 2px;
}
</style>