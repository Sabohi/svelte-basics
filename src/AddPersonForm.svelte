<script>
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    let name;
    let beltColour;
    let age;
    // let fighting = false;
    // let sneaking = false;
    // let running = false;
    let skills = [];
    const handleSubmit = () => {
        console.log(`${name} ${beltColour} ${age} ${skills}`);
        const person = { name, beltColour, age, skills, id: Math.random() };
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name} />
    <input type="number" placeholder="age" bind:value={age} />
    <label>Skills:</label>
    <!-- <input type="checkbox" bind:checked={fighting}/>Fighting <br/>
    <input type="checkbox" bind:checked={sneaking}/>Sneaking<br/>
    <input type="checkbox" bind:checked={running}/>Running <br/> -->
    <input type="checkbox" bind:group={skills} value="fighting"/>Fighting <br/>
    <input type="checkbox" bind:group={skills} value="sneaking"/>Sneaking<br/>
    <input type="checkbox" bind:group={skills} value="running"/>Running <br/>
    <label>beltColour:</label>
    <select bind:value={beltColour}>
        <option value="black">Black</option>
        <option value="brown">Brown</option>
        <option value="orange">Orange</option>
        <option value="white">White</option>
    </select>
    <button>Add Person</button>
</form>

<style>

</style>