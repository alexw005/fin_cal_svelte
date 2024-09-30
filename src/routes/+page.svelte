<script>
	import LoanCalculator from './LoanCalculator.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Financial calculator svelte app" />
</svelte:head>

<section class="flex flex-col items-center justify-center  h-screen p-8 gap-8 bg-cyan-100">
	<h1 class="text-4xl font-bold ">
		Loan Calculator
	</h1>
	<h2>
		Put the amount you want to borrow and the number of months you want to pay it back with the interest rate.
	</h2>
	<LoanCalculator />
</section>

