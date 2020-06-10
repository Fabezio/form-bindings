<script>
	import CustomInput from './CustomInput.svelte'
	import Toggle from './Toggle.svelte'
	// export let name;
	let val = ""
	let selectedOption = 2
	let price = 0
	let language = ["html"]

	let option = "frontend"
	let intro = false

	$:console.log(language)
	$:console.log(option)
	
</script>

<main>
	<h1>Bindings</h1>
	<div id="text">
		<CustomInput bind:val={val }  />
		<Toggle bind:chosenOption={selectedOption} />
		<!-- <hr> -->
		<div>{val || 'enter a value above'}</div>
		<br>
	</div>

	<div id="number">
		<input type='number' bind:value={price}>
		<div>${price}</div>
		<br>
	</div>

	<div id="checkbox">
		<label for="language"><input type="checkbox" bind:group={language} value="js"> js</label>
		<label><input type="checkbox" bind:group={language} value="html"> html</label>
		<label><input type="checkbox" bind:group={language} value="css"> css</label>
	</div>

	<div id="radio">
		<label for="radio"><input type="radio" bind:group={option} value='frontend'> frontend</label>
		<label for="radio"><input type="radio" bind:group={option} value='backend'> backend</label>
		<label for="radio"><input type="radio" bind:group={option} value='full stack'> full stack</label>
	</div>
	<button disabled={!language.length} on:click={() => intro = !intro}>introduce myself</button>
	{#if intro && language.length}
		 <!-- content here -->
	<h4>Hi, i'm a {option} web developer;
	i know {language.join(', ')} language{language.length > 1 ? "s" : ""}
	</h4>
	{/if}

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
	div {
		margin: 1rem;
	}
</style>