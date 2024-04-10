<script setup>
import { ref } from 'vue'

let num = ref (0)

</script>

<template >
  <div>
  <!-- navbar -->
  <nav class="navbar navbar-expand-lg nav-dark bg-body-tertiary">
  <div class="container-fluid">
    <router-link class="navbar-brand" to="/">
      <img src="./assets/icon.png" alt="Logo" height="24" class="d-inline-block align-text-center">
      PokeVite
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">Sobre</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>

  <!-- content -->
  <div class="main">
    <router-view></router-view>
  </div>
  <footer class="nav-dark bg-body-tertiary py-3 text-center">
    <div>
      <span>&copy{{new Date().getFullYear()}}</span>
    </div>
  </footer>
</div>
</template>

<style>
body{
  background: rgb(232,174,238);
background: radial-gradient(circle, rgba(232,174,238,0.4542191876750701) 0%, rgba(196,148,233,1) 100%);
}
footer{
  position: fixed;
  bottom: 0;
  width: 100%;
}
</style>