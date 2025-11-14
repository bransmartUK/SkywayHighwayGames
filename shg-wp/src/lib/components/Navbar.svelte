<script lang="ts">
  let lastScroll = 0;
  let hidden = false;

  function handleScroll() {
    const current = window.scrollY;
    hidden = current > lastScroll && current > 50;
    lastScroll = current;
  }

  if (typeof window !== "undefined") {
    window.addEventListener("scroll", handleScroll);
  }

  const scrollTo = (id: string) => {
    document.getElementById(id)?.scrollIntoView({ behavior: "smooth" });
  };
</script>

<nav class={`fixed top-0 left-0 w-full z-50 transition-transform duration-300 bg-black/70 backdrop-blur-md text-white ${hidden ? "-translate-y-full" : "translate-y-0"}`}>
  <div class="max-w-6xl mx-auto px-6 py-4 flex justify-between">
    <div class="font-bold text-xl cursor-pointer" on:click={() => scrollTo("hero")}>
      Skyway Highway Games
    </div>
    <div class="space-x-6 hidden md:flex">
      <button on:click={() => scrollTo("games")} class="hover:text-gray-300">Games</button>
      <button on:click={() => scrollTo("about")} class="hover:text-gray-300">About</button>
    </div>
  </div>
</nav>