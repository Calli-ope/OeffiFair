<script>
  import { goto } from '$app/navigation';
  import { MapPin, TrainFront, TrainTrack, Euro } from 'lucide-svelte';

  function handleClick() {
    goto('/endscreen');
  }
</script>

<main class="flex flex-col justify-center items-center h-screen bg-neutral-200">
  <div class="space-y-16 pb-20">
    <div class="text-4xl text-neutral-700 font-semibold">
      Hallo Max 👋
    </div>
    
    <div class="space-y-6">
      <div class="flex items-center space-x-3">
        <MapPin class="w-8 h-8 text-neutral-700" />
        <span class="font-medium text-2xl">Frohnau</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <TrainFront class="w-7 h-7 text-neutral-700" />
        <span class="font-medium text-xl">12 Haltestellen</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <TrainTrack class="w-7 h-7 text-neutral-700" />
        <span class="font-medium text-xl">16,7 km</span>
      </div>
      
      <div class="flex items-center space-x-3">
        <MapPin class="w-8 h-8 text-neutral-700" />
        <span class="font-medium text-2xl">Friedrichstraße</span>
      </div>
      
      <div class="flex items-center space-x-3 pt-5">
        <Euro class="w-7 h-7 text-neutral-700" />
        <span class="text-xl font-medium">2,70</span>
      </div>
    </div>
  </div>
  
  <button
    on:click={handleClick}
    class="fixed bottom-0 left-0 w-full px-6 py-3 text-neutral-100 text-xl bg-blue-500 rounded-lg hover:bg-blue-700 transition-colors"
  >
    Bis zum nächsten Ride!
  </button>
</main>