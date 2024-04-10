<template>
  <div class="col-4">
    <div class="card p-2 mb-3 cardList">
      <p class="text-center text-white">{{ pokemon.name }}</p>
      <img :src="urlBaseSvg" class="card-img-top" alt="..." height="80" />
    </div>
  </div>
</template>

<script setup>
const pokemon = defineProps(["name", "urlBaseSvg"]);
</script>

<style scoped>
.cardList {
  background: rgb(0, 14, 102);
  background: linear-gradient(
    90deg,
    rgba(0, 14, 102, 1) 0%,
    rgba(82, 0, 120, 0.2777485994397759) 0%,
    rgba(55, 0, 94, 0.2497373949579832) 100%,
    rgba(95, 147, 255, 0.4009978991596639) 100%
  );
  cursor: pointer;
}
.cardList:hover{
    background: rgb(0,14,102);
    background: linear-gradient(90deg, rgba(0,14,102,1) 0%, rgba(82,0,120,0.6362920168067228) 0%, rgba(55,0,94,0.6418942577030813) 100%, rgba(95,147,255,0.4009978991596639) 100%);
}
.cardList img:hover{
    padding: .3rem;
}
</style>