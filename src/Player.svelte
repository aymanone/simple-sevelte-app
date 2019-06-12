<script>
    //import Navebar from "./Navebar.svelte";
import {createEventDispatcher} from "svelte";
const dispatch=createEventDispatcher();
	export let name,points;
    
    let showControls=false;
    const addPoint=()=>{points++;}
    const removePoint=()=>{points--;}
    const toggleControl=()=>{showControls=!showControls;}
    const onDelete=()=>{
    dispatch("removeplayer",name);
    }
</script>

<style>
	p,h1 {
		color: purple;
	}
</style>


<div class="card">
<p>name: {name}</p>
<h1>points: {points}</h1>

<button on:click={toggleControl}>
{#if !showControls }show controls {:else} hide controls{/if}
</button>
<button on:click={onDelete}>delete it </button>

{#if showControls}
<button on:click={addPoint}>add point</button>
<button on:click={removePoint}>remove point</button>
<input type="number" bind:value={points}/>

{/if}
</div>

