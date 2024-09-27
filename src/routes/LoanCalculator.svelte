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

    function validate ()  {
        if (loan_amount <= 0 || loan_term <= 0 || interest <= 0) {
            console.log('Please enter valid values');
            return false;
        }
        return true;
    }

</script>

<main>
    <form onsubmit={validate} class="max-w-md mx-auto shadow-md rounded-lg p-6">
        <div class="flex flex-col gap-4">
          <div>
            <label for="loan_amount" class="block text-sm font-medium text-gray-700">Loan Amount</label>
            <input 
              type="number" 
              min="1" 
              required 
              id="loan_amount" 
              bind:value={loan_amount} 
              class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm invalid:border-red-500 invalid:focus:border-red-500 invalid:focus:ring-red-500"
              placeholder="Enter loan amount"
            />
          </div>
      
          <div>
            <label for="loan_term" class="block text-sm font-medium text-gray-700">Loan Term (Years)</label>
            <input 
              type="number" 
              min="1" 
              required 
              id="loan_term" 
              bind:value={loan_term} 
              class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm invalid:border-red-500 invalid:focus:border-red-500 invalid:focus:ring-red-500"
              placeholder="Enter loan term in years"
            />
          </div>
      
          <div>
            <label for="interest" class="block text-sm font-medium text-gray-700">Interest Rate (%)</label>
            <input 
              type="number" 
              min="0" 
              required 
              id="interest" 
              bind:value={interest} 
              class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm invalid:border-red-500 invalid:focus:border-red-500 invalid:focus:ring-red-500"
              placeholder="Enter interest rate"
            />
          </div>
      
          <div>
            <button 
              type="submit" 
              class="w-full bg-blue-600 text-white py-2 px-4 rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
            >
              Calculate
            </button>
          </div>
        </div>
    </form>
      
    {#if monthly_payment>0}<h2>Monthly Payment: ${monthly_payment.toFixed(2)}</h2>{/if}
</main>