<script lang="ts">
  import GameCard from "./GameCard.svelte";
  import ModalTrailer from "./ModalTrailer.svelte";
  import rogueCala from "$lib/assets/game/Roguecala.png";

  let showModal = false;
  let trailerSrc = "";

  const openTrailer = (src: string) => {
    trailerSrc = src;
    showModal = true;
  };

  const closeTrailer = () => {
    showModal = false;
    trailerSrc = "";
  };

  const games = [
    {
      title: "RogueCala",
      thumbnail: rogueCala,
      trailer: "https://www.youtube.com/embed/Kdq7e399kjQ?si=E8DDArVc7bT_yqc1"
    }
  ];
</script>

<section id="games" class="min-h-screen bg-black text-white py-24 px-6">
  <h1 class="text-4xl font-bold text-center mb-12">Our Games</h1>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-6xl mx-auto">
    {#each games as game}
      <GameCard {...game} onOpen={openTrailer} />
    {/each}
  </div>

  <ModalTrailer show={showModal} trailer={trailerSrc} onClose={closeTrailer} />
</section>