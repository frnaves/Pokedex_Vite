<script setup>

const pokemon = defineProps(["name", "base_experience", "height", "imagem", "loading"])

</script>


<template>

        <div class="card cardPokemonSelected">

            <img v-if="pokemon.name" :src="pokemon.imagem" class="card-img-top"             
            :class="loading ? '' : 'animate__animated animate__shakeY'" :alt="pokemon.name">

            <img v-else="" src="/src/assets/unown.png" 
            

            class="card-img-top pt-2"             
            :class="loading ? '' : 'animate__animated animate__shakeY'" :alt="pokemon.name">



            <div class="card-body">
                <h5 class="card-title text-center">{{pokemon.name || '???'}}</h5>
                <hr>
                <div class="row">
                    <section class="col">
                        <strong>XP: </strong>
                        <span>{{pokemon.base_experience}}</span>
                    </section>

                    <section class="col">
                        <strong>Altura: </strong>
                        <span>{{pokemon.height}}</span>
                    </section>
                </div>

            </div>            
        </div>          

</template>


<style scoped>

.cardPokemonSelected{
height: 75vh;
background: rgb(166,166,167);
background: linear-gradient(335deg, rgba(166,166,167,1) 0%, rgba(238,238,240,1) 60%, rgba(213,214,214,1) 100%);


}

</style>