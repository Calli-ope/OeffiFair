<script lang="ts">
  import { goto } from '$app/navigation';
  import { MapPin, TrainFront, TrainTrack, Euro, Loader } from 'lucide-svelte'; // Import necessary icons
  import { fade } from 'svelte/transition';
  import { onMount } from 'svelte';
  import BackButton from './BackButton.svelte';

  // State variables to control the visibility of loading icons and text for each item
  let showLocationLoading = false;
  let showLocation = false;

  let showHaltestellenLoading = false;
  let showHaltestellen = false;

  let showKmLoading = false;
  let showKm = false;

  let showPriceLoading = false;
  let showPrice = false;

  onMount(() => {
    // Sequence of displaying each item with loading and fade-in effect

    // 1. Frohnau
    setTimeout(() => {
      showLocationLoading = true;

      setTimeout(() => {
        showLocationLoading = false;
        showLocation = true;

        // 2. 12 Haltestellen
        setTimeout(() => {
          showHaltestellenLoading = true;

          setTimeout(() => {
            showHaltestellenLoading = false;
            showHaltestellen = true;

            // 3. 16,7 km
            setTimeout(() => {
              showKmLoading = true;

              setTimeout(() => {
                showKmLoading = false;
                showKm = true;

                  // 5. Preis (€)
                  setTimeout(() => {
                    showPriceLoading = true;

                    setTimeout(() => {
                      showPriceLoading = false;
                      showPrice = true;
                    }, 500); // Delay for Price
                  }, 0); // Delay before showing Price
            }, 100); // Delay before showing km
          }, 0); // Delay before showing km loading
        }, 500); // Delay before showing Haltestellen
      }, 0); // Delay before showing Haltestellen loading
    }, 500); // Delay before showing Location
  }, 200); // Initial delay before starting the sequence
});

  function handleClick() {
    goto('/endscreen');
  }
</script>

<main class="relative flex flex-col justify-center items-center h-screen bg-neutral-200">
  <!-- Back Button -->
  <BackButton />

  <div class="space-y-16 pb-20">
    <!-- Greeting -->
    <div class="text-4xl text-neutral-700 font-semibold">
      Hallo Max 👋
    </div>
    
    <!-- Journey Details -->
    <div class="space-y-6">
      <!-- Frohnau -->
      <div class="flex items-center space-x-3">
        <MapPin class="w-8 h-8 text-neutral-700" />
        {#if showLocationLoading}
          <!-- Loading Icon -->
          <Loader class="w-6 h-6 text-neutral-700 animate-spin" />
        {:else if showLocation}
          <!-- Faded-in Text -->
          <span transition:fade={{ duration: 500 }} class="font-medium text-2xl">Frohnau</span>
        {/if}
      </div>
      
      <!-- 12 Haltestellen -->
      <div class="flex items-center space-x-3">
        <TrainFront class="w-7 h-7 text-neutral-700" />
        {#if showHaltestellenLoading}
          <!-- Loading Icon -->
          <Loader class="w-6 h-6 text-neutral-700 animate-spin" />
        {:else if showHaltestellen}
          <!-- Faded-in Text -->
          <span transition:fade={{ duration: 500 }} class="font-medium text-xl">12 Haltestellen</span>
        {/if}
      </div>
      
      <!-- 16,7 km -->
      <div class="flex items-center space-x-3">
        <TrainTrack class="w-7 h-7 text-neutral-700" />
        {#if showKmLoading}
          <!-- Loading Icon -->
          <Loader class="w-6 h-6 text-neutral-700 animate-spin" />
        {:else if showKm}
          <!-- Faded-in Text -->
          <span transition:fade={{ duration: 500 }} class="font-medium text-xl">16,7 km</span>
        {/if}
      </div>
      
      <!-- Friedrichstraße -->
      <div class="flex items-center space-x-3">
        <MapPin class="w-8 h-8 text-neutral-700" />
        {#if showLocationLoading}
          <!-- Loading Icon -->
          <Loader class="w-6 h-6 text-neutral-700 animate-spin" />
        {:else if showLocation}
          <!-- Faded-in Text -->
          <span transition:fade={{ duration: 500 }} class="font-medium text-2xl">Friedrichstraße</span>
        {/if}
      </div>
      
      <!-- Price (€) -->
      <div class="flex items-center space-x-3 pt-5">
        <Euro class="w-7 h-7 text-neutral-700" />
        {#if showPriceLoading}
          <!-- Loading Icon -->
          <Loader class="w-6 h-6 text-neutral-700 animate-spin" />
        {:else if showPrice}
          <!-- Faded-in Text -->
          <span transition:fade={{ duration: 500 }} class="text-xl font-medium">2,70 €</span>
        {/if}
      </div>
    </div>
  </div>
  
  <!-- Navigation Button -->
  <button
    on:click={handleClick}
    class="fixed bottom-0 left-0 w-full py-4 text-white bg-blue-500 rounded-t-lg shadow-md transition-all duration-500 ease-in-out hover:bg-blue-600"
  >
    Bis zum nächsten Ride!
  </button>
</main>