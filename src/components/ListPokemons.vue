<script setup>

const pokemon = defineProps(["name", "urlBaseSvg"])

</script>


<template >
    <div class="col-4">    
        <div class="card p-1 mb-3  cardListPokemon">
            <p class="text-center">{{ pokemon.name }}</p>
            <img :src="urlBaseSvg" class="card-img-top" alt="..." height="90">
        </div>
    </div>
</template>


<style scoped>

.cardListPokemon{
    background: white;
    cursor: pointer;
    transition: background-color 1s ease;
}

.cardListPokemon img{
    transition: padding 0.3s ease;
}

.cardListPokemon:hover{
    background-color: rgba(166, 166, 167, 1);
}

.cardListPokemon img:hover{
    padding: 0.5rem;
}

</style>