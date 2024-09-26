<script lang="ts">

    let loan_term = $state(0);
    let interest = $state(0);
    let loan_amount = $state(0);
    // let monthly_payment = $state(0);
    const MONTHS_IN_YEAR = 12;
    const monthly_interest = $derived(interest / 100 / MONTHS_IN_YEAR);
    const number_of_payments =  $derived(loan_term * MONTHS_IN_YEAR);
    const x =  $derived(Math.pow(1 + monthly_interest, number_of_payments));
    const monthly_payment = $derived((loan_amount * x * monthly_interest) / (x - 1));
</script>

<main>
    <form>
        <div class="flex flex-col">
            <label for="loan_amount">Loan Amount</label>
            <input type="number" min="1" required id="loan_amount" bind:value={loan_amount} />
            <label for="loan_term">Loan Term</label>
            <input type="number" min="1" required id="loan_term" bind:value={loan_term} />
            <label for="interest">Interest Rate</label>
            <input type="number" min="0" required id="interest" bind:value={interest} />
            <button type="submit" >Calculate</button>
        </div>
    </form>
    {#if monthly_payment>0}<h2>Monthly Payment: ${monthly_payment.toFixed(2)}</h2>{/if}
</main>