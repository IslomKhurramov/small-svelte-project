<script>
	import Modal from './Modal.svelte';
    import Form from "./Form.svelte"
 let showModal=false
	 const toggleButton = ()=>{
		showModal= !showModal
	 }
	 let people=[
		{name:"Yoshi", age:"25",   id:"1"},
		{name:"Jimmy", age:"27", id:"2"},
		{name:"Kim", age:"24", id:"3"},
	 ]

	 const handleClick=(id)=>{
		people=people.filter((person)=>person.id !=id)
	 }

	const addPerson=(e)=>{
		const person = e.detail;
		people=[person, ...people];
		showModal=false;
	}
</script>


<Modal {showModal} on:click={toggleButton}>
  <Form on:addPerson={addPerson}/>
</Modal>
<main>
	<button on:click={toggleButton}>open modal</button>
{#each people as person (person.id)}
<div>
	<h4>{person.name}</h4>
	<p>{person.age} years old </p>
	<button on:click={()=>handleClick(person.id)}>delete</button>
</div>
{:else}
<p>there are no people to show ...</p>
{/each}

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>