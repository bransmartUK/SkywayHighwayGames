<script lang="ts">
  // Put your image at src/lib/assets/about/AboutImage.png (or change the path below)
  import aboutImg from "$lib/assets/BryanAlien.png";
</script>

<section id="about" class="min-h-screen bg-gray-900 text-white py-24 px-6">
  <div class="max-w-6xl mx-auto">
    <!-- Layout: mobile = column (text above image), md+ = row-reverse (image left, text right) -->
    <div class="flex flex-col md:flex-row-reverse items-center gap-8">
      <!-- Text (appears above image on mobile) -->
      <div class="w-full md:w-1/2">
        <h1 class="text-4xl font-bold mb-6">About Us</h1>
        <p class="text-lg leading-relaxed">
          Hey! We're Skyway Highway Games, i'm glad you were able to find us. We are a small indie game publishing / development company that wants to make
          the games that we truly wish we had to play ourselves, so if you got any taste like us, well you are in the right place!
          Team: Bryan Portieles - Founder / Developer
        </p>
      </div>

      <!-- Image (full width on mobile, left on desktop) -->
      <div class="w-full md:w-1/2 overflow-hidden rounded-lg shadow-lg">
        <img
          src={aboutImg}
          alt="About Skyway Highway Games"
          class="w-full h-fit md:h-fit object-cover"
        />
      </div>
    </div>
  </div>
</section>
<style>
  /* optional: tweak for very small screens */
  @media (max-width: 420px) {
    img { height: 220px; }
  }
</style>