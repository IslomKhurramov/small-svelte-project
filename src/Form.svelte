<script>
  import {createEventDispatcher} from "svelte";
  
  let dispatch = createEventDispatcher();
let name ;
let beltColor;
let age;
let skills=[];

const handleClick =()=>{
    const person ={
      name,
      beltColor,
      age,
      skills,
      id:Math.random()
    }
    dispatch("addPerson", person)
}
</script>

<div>
    <form on:submit|preventDefault={handleClick}>
        <input type="text" placeholder="name" bind:value={name}>
          <input type="number" placeholder="age" bind:value={age}>
          <!-- svelte-ignore a11y-label-has-associated-control -->
          <label>Skills:</label>
          <input type="checkbox" bind:group={skills} value="fighting">fighting <br>
          <input type="checkbox" bind:group={skills} value="running">running <br>
          <input type="checkbox" bind:group={skills} value="swimming">swimming <br>
          <!-- svelte-ignore a11y-label-has-associated-control -->
          <label >beltColor:</label>
          <select bind:value={beltColor}>
            <option value="black">black</option>
            <option value="yellow">yellow</option>
            <option value="green">green</option>
          </select>
         
        <button>Add a person</button>
    </form>
</div>