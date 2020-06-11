<script>
	import CustomInput from './CustomInput.svelte'
	import Toggle from './Toggle.svelte'
	import { isValidEmail } from './validation'
	// export let name;
	let val = "moi	"
	let selectedOption = 2
	let price = 0
	let language = ["html"]
	let school = 'udemy'

	let option = "frontend"
	let intro = false

	let usernameInput
	let newtext
	let customInput

	let email = ""
	let formIsValid = false
	$: if (isValidEmail(email)) {formIsValid = true
		}	else {formIsValid = false}
	
	function saveData() {
		// console.log(document.querySelector('#username').value)
		console.table(usernameInput)
		newtext=usernameInput.value
		customInput.empty()
		return newtext
	}


	$:console.log(email)
	$:console.log(option)
	
</script>

<main>
	<h1>Bindings</h1>
	<div id="text">
		<CustomInput bind:val bind:this={customInput} />
		<button on:click={saveData}>Save</button>
		<Toggle bind:chosenOption={selectedOption} />
		
		<div>{val || 'enter a value above'}</div>
		<br>
	</div>

	<!-- <div id="number">
		<input type='number' bind:value={price}>
		<div>${price}</div>
		<br>
	</div> -->

	<!-- <div id="checkbox">
		<label for="language"><input type="checkbox" bind:group={language} value="js"> js</label>
		<label><input type="checkbox" bind:group={language} value="html"> html</label>
		<label><input type="checkbox" bind:group={language} value="css"> css</label>
	</div>

	<div id="radio">
		<label for="radio"><input type="radio" bind:group={option} value='frontend'> frontend</label>
		<label for="radio"><input type="radio" bind:group={option} value='backend'> backend</label>
		<label for="radio"><input type="radio" bind:group={option} value='full stack'> full stack</label>
	</div>

	<div id="select">
		<select bind:value={school}>
			<option value='openclassrooms'> openclassrooms</option>
			<option value='codecademy'> codecademy</option>
			<option value='udemy'> udemy</option>
		</select>
	</div>
	<button disabled={!language.length} on:click={() => intro = !intro}>introduce myself</button>
	{#if intro && language.length}
	<h4>Hi, i'm a {option} web developer;
	i know {language.join(', ')} language{language.length > 1 ? "s" : ""}. <br>
	i've been learning on {school}.com 
	</h4>
	{:else if !language.length}
	<h4 class="red">you need to select at least one language</h4>
	{/if} -->

	<input type="text" id='username' bind:this={usernameInput} >
	<button on:click={saveData} >Save</button>
	<div>{newtext}</div>

	<hr>

	<form on:submit|preventDefault={email} >
		<input type="email" bind:value={email} class={isValidEmail(email) ? 'success' : 'error'}>
		<button type="submit" disabled={!formIsValid}>send data</button>
	</form>
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

	.red {color: red}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	div {
		margin: 1rem;
	}

	input {
		border-radius: .375em;
	}

	.success {
		border: 1.5px solid green;
	}
	.error {
		border: 1.5px solid red;
	}
</style>