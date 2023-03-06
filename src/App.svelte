<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';

	let showModal = false;

	// let firstName = 'Subuhi';
	// let lastName = 'Zaidi';
	// let beltColour = 'Black';

	// Reactive values
	// $: fullName = `${firstName} ${lastName}`;

	// Reactive statement
	// $: console.log(beltColour);
	// $: {
	// 	console.log(beltColour);
	// 	console.log(fullName);
	// }
	
	// const handleClick = () => {
	// 	beltColour = 'orange';
	// };

	// const handleInput = (e) => {
	// 	beltColour = e.target.value;
	// }

	const toggleModal = () => {
		showModal = !showModal;
	};

	let people = [
		{ name: 'yoshi', beltColour: 'black', age: 25, id: 1, skills:[] },
		{ name: 'mario', beltColour: 'orange', age: 45, id: 2, skills:[] },
		{ name: 'luigi', beltColour: 'brown', age: 35, id: 3, skills:[] }
	];

	const handleDelete = (id) => {
		people = people.filter(person => person.id != id);
	};

	const addPerson = (e) => {
		const person = e.detail;
		people = [person, ...people];
		showModal = false;
	};

	// let num = 6; // Try with 25 and 3
</script>

<!-- Conditionals  -->
<!--
{#if num > 20}
	<p>Greater than 20</p>
{:else if num > 5}
	<p>Greater than 5</p>
{:else}
	<p>Not greater than 5</p>
{/if} -->

<Modal {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson}/>
	<!-- <div slot="title">
		<h3>Add a new person</h3>
	</div> -->
</Modal>

<main>
	<!-- <button on:click|once={toggleModal}>Open modal</button> Event modifier = once/self/prevetDefault etc -->
	<button on:click={toggleModal}>Open modal</button> <!-- Event modifier = once/self/prevetDefault etc -->
	<!-- Each Loops - Each loop, unique id for linking data to DOm elements and else for checking empty data-->
	{#each people as person (person.id)}
		<h4>{person.name}</h4>
		{#each person.skills as skill}
			<p>{skill}</p>
		{:else}
			<p>No skills to show</p>
		{/each}
		{#if person.beltColour === 'black'}
			<p><strong>Master Ninja</strong></p>
		{/if}
		<p>{person.age} years old, {person.beltColour} belt.</p>
		<button on:click={() => handleDelete(person.id)}>Delete</button><!-- Inline Event Listeners -->
	{:else} 
		<p>There are no people to show...</p> <!-- Will run if people is an empty array -->
	{/each}
	<!-- <p>{fullName} - {beltColour} belt</p>
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName} /> -->
	<!-- <button on:click={handleClick}>Update belt colour</button> -->
	<!-- <input type="text" on:input={handleInput} value={beltColour} /> -->
	<!-- <input type="text" bind:value={beltColour} /> -->
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/* h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	} */

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>