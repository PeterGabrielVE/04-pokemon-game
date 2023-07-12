<template>
  <h1>¿Quien es este Pokemon?</h1>

  <PokemonPicture :pokemonId="4" :showPokemon="true"/>
  <PokemonOptions :pokemons="pokemonArr"/>

</template>

<script>
import PokemonPicture from '@/components/PokemonPicture.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'

import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
    components: {
        PokemonPicture,
        PokemonOptions
    },
    data(){
      return{
        pokemonArr: []
      }
    },
    methods:{
      mixPokemonArray(){
        this.pokemonArr = getPokemonOptions()
        console.log(this.pokemonArr)
      }
    },
    mounted(){
      this.mixPokemonArray()
    }

}
</script>

<style>

</style>