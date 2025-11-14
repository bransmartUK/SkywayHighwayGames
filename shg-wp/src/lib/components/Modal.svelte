<script>
  export let open = false;
  export let onClose = () => {};

  // Pass an array like:
  // [
  //   { type: "image", src: "/assets/my-image.png" },
  //   { type: "video", src: "/assets/trailer.mp4" }
  // ]
  export let media = [];

  export let steamUrl = "#";

  let selected = media[0];
  const selectMedia = (item) => (selected = item);
</script>

{#if open}
<div class="fixed inset-0 bg-black/60 backdrop-blur-sm flex items-center justify-center z-50" on:click={onClose}>
  <div class="bg-neutral-900 text-white w-[90%] max-w-5xl rounded-xl overflow-hidden shadow-xl flex" on:click|stopPropagation>

    <!-- LEFT SIDE: Selected media -->
    <div class="w-1/2 bg-black flex items-center justify-center p-4">
      {#if selected.type === "image"}
        <img src={selected.src} alt="Selected" class="max-h-[80vh] object-contain rounded-lg" />
      {:else if selected.type === "video"}
        <video 
          src={selected.src} 
          controls 
          autoplay 
          class="max-h-[80vh] object-contain rounded-lg"
        />
      {/if}
    </div>

    <!-- RIGHT SIDE: Gallery & Steam button -->
    <div class="w-1/2 bg-neutral-800 flex flex-col p-4">

      <!-- Gallery grid -->
      <div class="grid grid-cols-3 gap-3 overflow-y-auto pr-2 flex-grow">
        {#each media as item (item.src)}
          <!-- thumbnail wrapper: fixed aspect ratio using padding-top trick for consistent shape -->
          <div
            class=" max-h-fit cursor-pointer rounded-lg overflow-hidden border transition"
            on:click={() => selectMedia(item)}
            class:selected={item === selected}
            aria-pressed={item === selected}
            style="border-color: rgba(255,255,255,0.12);"
          >
            <div style="position:relative;width:100%;padding-top:66.666%;"> <!-- 3:2 aspect -->
              {#if item.type === "image"}
                <img
                  src={item.src}
                  alt=""
                  style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover;"
                />
              {:else if item.type === "video"}
                <video
                  src={item.src}
                  muted
                  style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover;"
                />
              {/if}
            </div>

            <!-- visual active indicator -->
            {#if item === selected}
              <div class="absolute inset-0 pointer-events-none ring-2 ring-blue-500 rounded-lg" style="mix-blend-mode:screen"></div>
            {/if}
          </div>
        {/each}
      </div>

      <!-- Bottom Steam button -->
      <div class="pt-4">
        <a 
          href={steamUrl} 
          target="_blank"
          class="block text-center bg-blue-600 hover:bg-blue-700 transition p-3 rounded-lg font-semibold"
        >
          View on Steam
        </a>
      </div>

    </div>
  </div>

  <!-- Close area -->
  <button 
    class="absolute top-4 right-4 bg-white/20 hover:bg-white/40 text-white p-2 rounded-full"
    on:click={onClose}
  >
    ✕
  </button>
</div>
{/if}

<style>
  /* small visual for selected thumbnail */
  .selected {
    box-shadow: 0 0 0 3px rgba(59,130,246,0.25);
    border-color: rgba(59,130,246,0.6) !important;
  } 
</style>