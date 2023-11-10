<script>
   
    /**
   * @type {{ image: any; name: any; id: any; }}
   */
     export let pokemon ; // data prop

     import { fade } from 'svelte/transition';
</script>
<style>
    /* .Card{
        background-color: rgb(103, 43, 43);
        text-align: center;
        border-radius: 20px;
        flex: content;
        align-items: center;
    } */
 
</style>

<a href={`./pokemon/${pokemon.id}`}
transition:fade>
    
    <img class="h-40 w-40" src={pokemon.image} alt={pokemon.name}>
    <h2 class="text-2xl"> {pokemon.id}. {pokemon.name}</h2>

   
</a>
