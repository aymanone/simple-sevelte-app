<script>
    import Navebar from "./Navebar.svelte";
    import Player from "./Player.svelte";
    import AddPlayer from "./AddPlayer.svelte";
	//export let name,age;
    let players=[
    {name:"ayman",points:100},

    {name:"adham",points:100},
    {name:"pele",points:100}
    ]
    const addPlayer=(e)=>{
    // data in e.detail
    const newPlayer=e.detail;
    
    players=[...players,newPlayer];
    };
    const removePlayer=(e)=>{
    
    players=players.filter(player=>player.name!==e.detail);
    
    
    };
    
</script>

<Navebar />
<div class="container">
<AddPlayer on:addplayer={addPlayer} />
{#if players.length!==0}
{#each players as player}
<Player name={player.name} points={player.points} on:removeplayer={removePlayer} />
{/each}
{:else}
<p>no players</p>
{/if}

</div>
