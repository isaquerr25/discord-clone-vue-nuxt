<script setup lang="ts">
   import Header from '@/components/Global/Header/index.vue'
  import Footer from '@/components/Global/Footer/index.vue'

  defineProps(['error'])
</script>
<template >
  <div class="min-h-screen flex flex-col bg-blue-700">
    <Header />

    <main class="bg-white flex-1 grid place-items-center">

      <section class="w-full max-w-4xl flex flex-col items-center justify-between p-6 sm:flex-row sm:items-start sm:p-16">

        <section>
        <article>
          <h2 class="archivo text-blue-700 font-black text-4xl sm:text-5xl md:text-4xl">Page not found</h2>

          <p class="mt-4">Page not found, due to being a clone, only the <span class="text-blue-700 font-bold">login </span>and <span class="text-blue-700 font-bold">home </span>pages are available for access</p>
        </article>
        <article class="py-4 flex gap-2 underline text-lg">
          <nuxt-link to="/">Home</nuxt-link>
          <nuxt-link to="/login">Login </nuxt-link>
        </article>
 
        </section>
       
        <img src="@/static/svg/discord_assets/not_found.gif" class="w-96"/>
      </section>
    </main>

    <Footer />
  </div>
</template>