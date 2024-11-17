<script setup>

const pokemon = defineProps(["name", "base_experience", "height", "imagem", "loading", "number", "cry"])


</script>


<template>   

        <div class="card cardPokemonSelected">

            <img v-if="pokemon.name" :src="pokemon.imagem" class="card-img-top"             
            :class="loading ? '' : 'animate__animated animate__shakeY'" :alt="pokemon.name">

            <img v-else="" src="/src/assets/unown.png" 
            

            class="card-img-top pt-2"             
            :class="loading ? '' : 'animate__animated animate__shakeY'" :alt="pokemon.name">



            <div class="card-body" style="text-align: center;">
                <h5 class="card-title text-center">{{pokemon.name || '???'}}</h5>
                <hr>
                <div class="row" style="font-size: small; align-items: center;">
                    <section class="col">
                        <strong>Nº: </strong>
                        <span>{{pokemon.number}}</span>
                    </section>

                    <section class="col">
                        <strong >XP: </strong>
                        <span>{{pokemon.base_experience}}</span>
                    </section>

                    <section class="col">
                        <strong>Altura: </strong>
                        <span>{{pokemon.height}}</span>
                    </section>


                    <section class="col">
                        <audio id="player" :src="cry"></audio>

                        <button class="btn btn-light" onclick="document.getElementById('player').play()"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-soundwave" viewBox="0 0 16 16">
  <path fill-rule="evenodd" d="M8.5 2a.5.5 0 0 1 .5.5v11a.5.5 0 0 1-1 0v-11a.5.5 0 0 1 .5-.5m-2 2a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5m4 0a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5m-6 1.5A.5.5 0 0 1 5 6v4a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5m8 0a.5.5 0 0 1 .5.5v4a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5m-10 1A.5.5 0 0 1 3 7v2a.5.5 0 0 1-1 0V7a.5.5 0 0 1 .5-.5m12 0a.5.5 0 0 1 .5.5v2a.5.5 0 0 1-1 0V7a.5.5 0 0 1 .5-.5"/>
</svg></button>


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

.cardPokemonSelected img {
    margin-top: 50px;
    height: 250px;
    width: auto; 
    object-fit: contain;
}

@media (max-width: 1000px) {

    .cardPokemonSelected{
    height: 35vh;
    margin: 0 0 10px 0;
    }

    .cardPokemonSelected img {
    margin-top: 27px;
    height: 100px;
    width: auto; 
    object-fit: contain;
    }

}

</style>