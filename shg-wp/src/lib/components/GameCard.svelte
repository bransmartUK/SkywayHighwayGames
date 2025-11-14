<script lang="ts">
  export let title: string;
  export let thumbnail: string;
  export let trailer: string;
  export let onOpen: (src: string) => void;
</script>

<div class="bg-gray-800 rounded-xl p-4 hover:scale-105 transition cursor-pointer border border-gray-700"
     on:click={() => onOpen(trailer)}>
  <img src={thumbnail} alt={title} class="rounded-md w-full h-48 object-cover mb-4" />
  <h2 class="text-white text-lg font-bold">{title}</h2>
</div>