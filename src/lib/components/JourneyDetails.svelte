<script>
  import { MapPin, TrainFront, TrainTrack, Euro } from 'lucide-svelte';
  import { fade } from 'svelte/transition';

  let showEndScreen = false;

  function handleClick() {
    setTimeout(() => {
      showEndScreen = true;
    }, 500);
  }
</script>

{#if !showEndScreen}
<main class="flex flex-col justify-center items-center h-screen bg-neutral-200">
  <div class="space-y-16 pb-20">
    <div class="text-3xl font-semibold">
      Hallo Max 👋
    </div>
    
    <div class="space-y-6">
      <div class="flex items-center space-x-3">
        <MapPin class="w-7 h-7 text-gray-500" />
        <span class="font-medium text-xl">Frohnau</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <TrainFront class="w-6 h-6 text-gray-500" />
        <span>12 Haltestellen</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <TrainTrack class="w-6 h-6 text-gray-500" />
        <span>16,7 km</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <MapPin class="w-7 h-7 text-gray-500" />
        <span class="font-medium text-xl">Friedrichstraße</span>
      </div>
      
      <div class="flex items-center space-x-3 pt-5">
        <Euro class="w-6 h-6 text-gray-500" />
        <span class="text-xl font-medium">2,70 €</span>
      </div>
    </div>
  </div>
  
  <button
    on:click={handleClick}
    class="fixed bottom-0 left-0 w-full px-6 py-3 text-white bg-blue-500 rounded-lg hover:bg-blue-700 transition-colors"
  >
    Bis zum nächsten Ride!
  </button>
</main>
{:else}
  <div class="min-h-screen bg-neutral-200 p-6 flex flex-col justify-center items-center" in:fade={{ duration: 300 }}>
    <h1 class="text-3xl font-semibold mb-4">ÖffiFair</h1>
    <p class="text-xl text-gray-600">Thank you for your ride!</p>
  </div>
{/if}