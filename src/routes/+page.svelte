<script>
	import Counter from './Counter.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="flex flex-col items-center justify-center  min-h-screen p-8 gap-8">
	<h1 class="text-4xl font-bold ">
		Loan Calculator
	</h1>
	<h2>
		Put the amount you want to borrow and the number of months you want to pay it back with the interest rate.
	</h2>
	<Counter />
</section>

