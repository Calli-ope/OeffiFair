<script lang="ts">
    import { goto } from '$app/navigation';
    import { ChevronLeft } from 'lucide-svelte'; // Import an icon for the back button
  
    function handleBack() {
      goto('/');
    }
</script>

<button
    on:click={handleBack}
    class="absolute top-4 left-4 p-2 rounded-full text-neutral-700 hover:bg-neutral-300"
    >
    <ChevronLeft class="w-8 h-8" />
</button>