<script setup>

import { onMounted, reactive, ref, computed } from 'vue';
import ListPokemons from '@/components/ListPokemons.vue';
import CardPokemonSelected from '@/components/CardPokemonSelected.vue';

let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/")
let pokemons = reactive(ref())
let searchPokemonField = ref("")
let pokemonSelected = reactive(ref())
let loading = ref(false)

onMounted(()=>{
  fetch("https://pokeapi.co/api/v2/pokemon?limit=1025&offset=0")
  .then(res => res.json())
  .then(res => pokemons.value = res.results);  
})


const pokemonsFiltered = computed(() => {
  if(pokemons.value && searchPokemonField.value){
    return pokemons.value.filter(pokemon=>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    )
  }
  return pokemons.value;
})

const selectPokemon = async (pokemon)=>{
  loading.value = true;
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res => pokemonSelected.value = res)
  .catch(err => alert(err))
  .finally(()=>{ loading.value = false; })

  console.log(pokemonSelected.value)
}

</script>

<template>
  <main>
    <div class="container text-body-secondary">
      <div class="row mt-2">     
        
        <div class="col-sm-12 col-md-12 col-lg-6">          
          <CardPokemonSelected 
          :name = "pokemonSelected?.name" 
          :base_experience = "pokemonSelected?.base_experience"
          :height = "pokemonSelected?.height"
          :imagem = "pokemonSelected?.sprites.other.showdown.front_default" 
          :loading="loading"
          :number ="pokemonSelected?.id"
          :cry = "pokemonSelected?.cries.latest"

          />
        </div>


        <div class="col-sm-12 col-md-12 col-lg-6">         
          <div>
            <div class="input-group mb-2 pesquisa">
                <span class="input-group-text" id="inputGroup-sizing-default"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16"><path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001q.044.06.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1 1 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0"/></svg></span>
                
                <label 
                hidden 
                for="searchPokemonField">
                </label>

                <input 
                v-model = searchPokemonField
                type="text" 
                id="searchPokemonField" 
                class="form-control"
                placeholder="Pesquisar">

              </div>

          </div>           
 
          <div class="card cardList">  
            
            <div class="card-body row ">
              
              
              <ListPokemons 
              v-for="pokemon in pokemonsFiltered"
              :key="pokemon.name"
              :name = "pokemon.name"
              :urlBaseSvg= "urlBaseSvg + pokemon.url.split('/')[6] + '.png'"
              @click="selectPokemon(pokemon)"
              />
            </div>
          </div>
        </div>                 

      </div>
    </div>
    
  </main>
</template>

<style scoped>

.cardList{
  max-height: 75vh;

  overflow-y: scroll;
  overflow-x: hidden;
}

@media (max-width: 1000px) {
  .cardList{
  max-height: 45vh;
}
  
}


.pesquisa{
  height: 40px;
}

</style>