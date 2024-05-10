<script>

    import Character from './lib/character.svelte';

  let characters =[];
  let page = 1;
 async function loadcharacters(){
  const response = await fetch('https://rickandmortyapi.com/api/character?page=' + page);
  const data = await response.json();
  characters = data.results;

}
loadcharacters();

function nextpage(){
  page++;
  loadcharacters()

}
function previouspage(){
  page--;
  loadcharacters()

}

</script>


<h1 class="tible">rick and morty </h1>

 <div  class="container">
<div class="btns">
    <button class="btn" on:click={previouspage} disabled={page===1}> previous</button>
    <button class="btn" on:click={nextpage}> next</button>
</div>

  <div class="grid">
    {#each  characters as character} 
       <Character character={character}/>
 {/each}
</div>
</div>