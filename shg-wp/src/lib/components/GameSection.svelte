<script lang="ts">
  import GameCard from "./GameCard.svelte";
  import Modal from "./Modal.svelte";

  // Import thumbnails/media
  import rogueCalaThumb from "$lib/assets/game/Roguecala/Roguecala.png";
  import rogueCalaImg1 from "$lib/assets/game/Roguecala/Roguecala.png"; 
  import comingSoonThumb from "$lib/assets/game/ComingSoon/ComingSoonPlaceHolder.png";

  // import yourGameThumb from "$lib/assets/game/YourGame.png";
  // import yourGameImg1 from "$lib/assets/game/YourGame.png";
  // Add more imports as needed

  let showModal = false;
  let activeGame = null;

  // FULL MULTI-GAME DATA
  const games = [
    {
      id: "roguecala",
      title: "Roguecala",
      thumbnail: rogueCalaThumb,
      gallery: [
        { type: "image", src: rogueCalaImg1 },
        // Add more:
        // { type: "video", src: "/videos/roguecala-trailer.mp4" }
      ],
      steamUrl: "https://store.steampowered.com/app/123456/Roguecala/"
    },

    {
      id: "comingsoon",
      title: "Coming Soon!",
      thumbnail: comingSoonThumb,
      gallery: [
        { type: "image", src: comingSoonThumb }
      ],
      steamUrl: "https://store.steampowered.com/app/999999/Your_Game/"
    }
  ];

  const openGameModal = (game) => {
    activeGame = game;
    showModal = true;
  };

  const closeModal = () => {
    showModal = false;
    activeGame = null;
  };
</script>

<section id="games" class="min-h-screen bg-black text-white py-24 px-6">
  <h1 class="text-4xl font-bold text-center mb-12">Our Games</h1>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-6xl mx-auto">
    {#each games as game}
      <GameCard 
        title={game.title}
        thumbnail={game.thumbnail}
        onOpen={() => openGameModal(game)}
      />
    {/each}
  </div>

  {#if activeGame}
    <Modal
      open={showModal}
      onClose={closeModal}
      media={activeGame.gallery}
      steamUrl={activeGame.steamUrl}
    />
  {/if}
</section>