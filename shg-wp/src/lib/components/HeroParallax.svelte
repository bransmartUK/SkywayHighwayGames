<script lang="ts">
  import hero from "$lib/assets/background/FullArt.png";
  let offset = 0;

  function handleScroll() {
    offset = window.scrollY * 0.4;
  }

  if (typeof window !== "undefined") {
    window.addEventListener("scroll", handleScroll);
  }
</script>
<section id="hero" class="h-screen w-full relative overflow-hidden">
  <div class="absolute inset-0 bg-cover bg-center" style="background-image: url('{hero}'); transform: translateY({offset}px);"></div>
<!-- black overlay -->
  <div class="absolute inset-0 bg-black/60 pointer-events-none"></div>

  <div class="relative h-full flex flex-col items-center justify-center text-white text-center px-6">
    <h1 class="text-5xl font-bold drop-shadow-lg">Skyway Highway Games</h1>
    <p class="text-xl mt-4 drop-shadow-md">Making the games we've always wanted to play</p>
  </div>
</section>

