<script>
	import Header from '../components/Header.svelte';
	import '../app.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>
	
</div>

