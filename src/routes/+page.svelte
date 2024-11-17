<script lang="ts">
  import { goto } from '$app/navigation';
  import { MapPin, Loader } from 'lucide-svelte'; // Import icons

  let loading = false;
  let currentStep = 0; // Represents the current step in the sequence

  function handleStart() {
    loading = true;
    currentStep = 1; // 'Eingestiegen in Frohnau'

    setTimeout(() => {
      currentStep = 2; // 'Fahrt läuft...'

      setTimeout(() => {
        currentStep = 3; // 'Ausgestiegen in Friedrichstraße'

        setTimeout(() => {
          goto('/mainscreen');
        }, 3000);
      }, 5000);
    }, 3000);
  }
</script>

{#if !loading}
<main class="flex flex-col justify-center items-center h-screen bg-neutral-200">

  <div class="absolute top-0 w-full flex justify-center mt-24">
    <img src="/Icon.png" alt="App Icon" class="w-36 h-36" />
  </div>

  <h1 class="font-bold text-5xl text-neutral-700 mb-8">ÖffiFair</h1>
  <button on:click={handleStart} class="px-8 py-4 text-neutral-100 text-xl bg-blue-500 rounded-lg hover:bg-blue-700 transition-colors">
    Start
  </button>
</main>
{:else}
<div class="flex flex-col justify-center items-center h-screen bg-neutral-200">
  {#if currentStep === 1}
    <div class="flex flex-col items-center space-y-10">
      <MapPin class="w-16 h-16 text-neutral-700" />
      <p class="text-2xl text-neutral-700 text-center">
        Eingestiegen in <span class="font-bold">Frohnau</span>
      </p>
    </div>
  {:else if currentStep === 2}
    <div class="flex flex-col items-center space-y-10">
      <Loader class="w-16 h-16 text-neutral-700 animate-spin" />
      <p class="text-2xl text-neutral-700 text-center">
        Fahrt läuft...
      </p>
    </div>
  {:else if currentStep === 3}
    <div class="flex flex-col items-center space-y-10">
      <MapPin class="w-16 h-16 text-neutral-700" />
      <p class="text-2xl text-neutral-700 text-center">
        Ausgestiegen in <span class="font-bold">Friedrichstraße</span>
      </p>
    </div>
  {/if}
</div>
{/if}