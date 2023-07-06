<script lang="ts">
	import { Toaster, toast } from 'svelte-sonner';

	let beshyTextInput: string = '';

	$: beshyText = beshyTextInput.replace(/\s/g, ' 🤸‍♀️ ');
</script>

<svelte:head>
	<title>Beshify</title>
	<meta
		name="description"
		content="An easy way to write beshy text. You use it to ask someone, typically a friend of yours, why they are sad."
	/>
	<meta name="keywords" content="beshy ko, beshify" />
	<meta name="author" content="Peter John Arao" />
	<meta name="og:title" content="Beshify" />
	<meta
		name="og:description"
		content="An easy way to write beshy text. You use it to ask someone, typically a friend of yours, why they are sad."
	/>
	<meta property="og:site_name" content="Beshify" />
</svelte:head>

<main class="container">
	<Toaster richColors position="bottom-right" />
	<h1 class="heading">Beshify</h1>
	<p>
		An easy way to write beshy text. You use it to ask someone, typically a friend of yours, why
		they are sad
	</p>
	<div class="inputs">
		<form>
			<input type="text" bind:value={beshyTextInput} placeholder="Enter your beshy text" />
			<div class="content">
				{#if beshyText}
					<p class="beshy-text">{beshyText}</p>
					<button
						on:click={() => {
							toast.success(beshyText + ' copied to clipboard!');
							navigator.clipboard.writeText(beshyText);
						}}>Copy</button
					>
				{/if}
			</div>
		</form>
	</div>
	<footer>
		<p class="footer-text">Made with <span>&#10084;</span> by pitzzahh</p>
		<p class="footer-text">Under Construction &#9881;</p>
	</footer>
</main>
