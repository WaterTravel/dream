<script>
  import Counter from "./Counter.svelte";



 
  import PokemonCard from '../components/pokemonCard.svelte';
import {arrPokemon} from  './stores/pokestore'
import Pokedex from '$lib/images/Pokedex.png';
//   import type { applyAction } from "$app/forms";
import App from './App.svelte';
  

let searchTerm=''
  /**
   * @type {any[]}
   */
let filteredPokemon =[];

//reactivity
// $:{
    
//     if (searchTerm) {
//         filteredPokemon =
// $arrPokemon.filter(pokemon => pokemon.name.includes(searchTerm))
//     } else (
//         filteredPokemon=[...$arrPokemon]
//     )
// }


$: filteredPokemon = searchTerm
    ? $arrPokemon.filter(pokemon => pokemon.name.includes(searchTerm))
    : [...$arrPokemon];
</script>




<svelte:head>
	<title>Wontaek PokeWiki</title>
	<meta name="description" content="Svelte demo app" />
    
</svelte:head>



<!-- svelte-ignore a11y-missing-attribute -->

<img src="{Pokedex}">

<App></App>




<!-- <h1 class="text-4xl font-bold text-center my-10 underline">포켓몬 위키 사이트</h1> -->


<span class="text-4xl font-bold text-center my-10 "> 당신이 찾는 포켓몬은?</span>
<!-- <span class="text-3xl my-8 text-center "> 당신이 찾는 포켓몬은?</span> -->
<input class= "w-full rounded-md text-lg p-4 mb-8 border-6 border-black-500" type="text" bind:value={searchTerm} placeholder="포켓몬검색">

<div class="grid gap-7 md:grid-cols-6 grid-cols-3 ">
   
{#each filteredPokemon as pokemon}
<PokemonCard {pokemon} ></PokemonCard>
{/each}

</div>