<script>
	export let name;
	import Person from './Person.svelte';
	let randomResult; // no export == private
	$: result = Math.round(randomResult * 100); //? 'winner' : 'loser'; // dollar syntax for auto-bind
	function setRandom() {
	  randomResult = Math.random();
	}
	let data = {
	    userId: 123456,
	    name: 'Fred',
	    email: 'Fred@Test.com'
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {data.name}!</h1>
<Person {...data} />
<hr>
<p>The random number is {randomResult}</p>
<hr>
<p>{ result }</p>
<p>{ result }</p>
<button on:click={setRandom}>Randomize</button>
<input bind:value={randomResult}>

<p>Your score is { result }</p>
{#if result > 75}
    <p>Big Winner! Top 25%</p>
{:else if result > 50 }
    <p>Decent, top 50%</p>
{:else}
    <p>Loser</p>
{/if}