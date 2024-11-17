<script setup>

import { ref } from 'vue'

let num = ref(0)

</script>

<template>
  <nav class="navbar navbar-expand-lg ">
    <div class="container-fluid bg-secondary-subtle p-1">
      
      <router-link class="navbar-brand" to="/">      
        <img src="/src/assets/pokevite.png" alt="Logo" width="30" height="30"><strong>PokeVite</strong>
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
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
        </ul>
      </div>

    </div>
  </nav>

  <!-- Content -->
  <div class="main">
    <router-view>
      
    </router-view>
  </div>


  <!-- Footer --> 

  <footer class="bg-body-tertiary text-center text-lg-start">
  <!-- Copyright -->
  <div class="text-center p-2" style="background-color: rgba(0, 0, 0, 0.05)">
    © {{ new Date().getFullYear() }} - Desenvolvido por Felipe Naves </div>
  <!-- Copyright -->
  </footer>

</template>


<style>

.navbar{
  
  display: block;
  font-size: small;
  margin-top: 0px;
  padding-top: 0px;
}

footer{
  padding-top: 10px;
  position: fixed;
  bottom: 0;
  width: 100%;
  align-items: center;
  justify-content: center;
}


</style>