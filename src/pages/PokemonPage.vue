<template>
  <h1 v-if="!pokemon">Espere por favor....</h1>
  <div v-else>
    <h1>¿Quien es este Pokemon?</h1>
    <PokemonPicture :pokemon-id="pokemon.id"  :showPokemon="true"/>
    <PokemonOptions :pokemons="pokemonArr"/>
  </div>


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
        pokemonArr: [],
        pokemon: null,
        showPokemon: false,
        showAnswer: false,
        message: ''
      }
    },
    methods:{
      async mixPokemonArray(){
        this.pokemonArr = await getPokemonOptions()

            const rndInt = Math.floor( Math.random() * 4 )
            this.pokemon = this.pokemonArr[ rndInt ]
      }
    },
    mounted(){
      this.mixPokemonArray()
    }

}
</script>

<style>

</style>