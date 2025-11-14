<script lang="ts">
  export let show = false;
  export let trailer = "";
  export let onClose: () => void;
</script>

{#if show}
<div class="fixed inset-0 bg-black/70 backdrop-blur-md flex justify-center items-center z-50">
  <div class="bg-black p-4 rounded-xl max-w-3xl w-full relative">
    <button class="absolute top-2 right-2 text-white text-2xl" on:click={onClose}>×</button>

    <iframe
      class="w-full aspect-video rounded-lg"
      src={trailer}
      title="Trailer"
      allowfullscreen
    ></iframe>
  </div>
</div>
{/if}