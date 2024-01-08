<script setup lang="ts"></script>

<template>
  <div class="absolute hidden layout z-0 sm:block">
    <img
      src="../../../static/svg/discord_assets/background_large.svg"
      class="img-bg m-auto"
    />

    <section class="absolute inset-1 flex overflow-hidden justify-center">
      <img
        class="img-sm mr-80"
        src="../../../static/svg/discord_assets/hang_out.svg"
      />
      <img
        class="img-sm ml-80"
        src="../../../static/svg/discord_assets/conversation.svg"
      />
    </section>
  </div>
</template>

<style scoped>
.img-bg {
  width: 100%;
  overflow: hidden;
  height: 40rem;
  object-fit: cover;
}

.img-sm {
  width: 40rem;
  object-fit: contain;
  margin-top: auto;
}
</style>
