<script>
  import { MapPin, User, Tag, Euro } from 'lucide-svelte';
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
  <div class="space-y-6 pb-20"> <!-- Add padding to avoid overlap with the button -->
    <div class="text-2xl font-semibold">
      Hallo Max 👋
    </div>
    
    <div class="space-y-4">
      <div class="flex items-center space-x-3">
        <MapPin class="w-5 h-5 text-gray-500" />
        <span class="font-medium">Frohnau</span>
      </div>
      
      <div class="pl-8 space-y-2">
        <div class="flex items-center space-x-3">
          <User class="w-5 h-5 text-gray-500" />
          <span>12 Haltestellen</span>
        </div>
        
        <div class="flex items-center space-x-3">
          <Tag class="w-5 h-5 text-gray-500" />
          <span>16,7 km</span>
        </div>
        
        <div class="flex items-center space-x-3">
          <MapPin class="w-5 h-5 text-gray-500" />
          <span class="font-medium">Friedrichstraße</span>
        </div>
      </div>
      
      <div class="flex items-center space-x-3">
        <Euro class="w-5 h-5 text-gray-500" />
        <span class="text-2xl font-bold">2,70 €</span>
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
  <div class="min-h-screen bg-white p-6 flex flex-col justify-center items-center" in:fade={{ duration: 300 }}>
    <h1 class="text-3xl font-semibold mb-4">ÖffiFair</h1>
    <p class="text-xl text-gray-600">Thank you for your ride!</p>
  </div>
{/if}