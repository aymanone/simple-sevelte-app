<script>
import {createEventDispatcher} from "svelte";
const dispatch=createEventDispatcher();
let player={
name:"",points:0
};
const onSubmit=(e)=>{
  e.preventDefault();
  if (player.name.length===0 || player.points<0){
  alert("invalid name or number of points");
  return false;
  }
  dispatch("addplayer",player);
  player={
name:"",points:0
};
};
</script>
<form on:submit={onSubmit}>
<input type="text" bind:value={player.name} placeholder="player name" required/>
<input type="number" bind:value={player.points} placeholder="player points" required/>
<input type="submit" value="add player">
</form>