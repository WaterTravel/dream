<script>
      import {arrPokemon} from '../../../routes/stores/pokestore'
 
    export let data;
    const {pokemon} = data;
</script>


<h1 class="text-5xl my-8 text-center text-aquamarine-700">포켓몬 상세페이지</h1>

<div class="flex flex-col text-center items-center text-4xl my-6">
    <h1 class="text-4xl text-center my-4">{pokemon.name}</h1>
    <h1 class="text-4xl text-center my-4">{$arrPokemon[pokemon.id-1].name}</h1>
    
    <p >타입 : {pokemon.types[0].type.name}
    {#if pokemon.types.length > 1}
    {#if pokemon.types[1]} , {pokemon.types[1].type.name} {/if}
  {/if}
</p>

    <p>키 : {pokemon.height}</p>
    <p>무게 : {pokemon.weight}</p>
    <p>특성 : {pokemon.abilities}</p> 
    <!-- <p>특성 : {pokemon.abilities}</p>  -->
   <!-- <p>기술 : {pokemon.moves}</p> -->
   
    
    <div class="flex justify-center content-center  my-10 items-center">
    <img class="h-80 w-80" src={pokemon.sprites['front_default']}
    alt={pokemon.name}>
    <img class="h-80 w-80" src={pokemon.sprites['back_default']}
    alt={pokemon.name}>
     <img class="h-80 w-80" src={pokemon.sprites['front_shiny']}
    alt={pokemon.name}>
    <img class="h-80 w-80" src={pokemon.sprites['back_shiny']}
    alt={pokemon.name}>
</div>

</div>