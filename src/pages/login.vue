<script setup lang="ts">
  import Background  from '@/components/Home/Background/index.vue'
</script>
<template>
  <div class="bg-blue-700 w-full h-screen p-2  grid place-items-center">

    <Background />
    <main class="z-20 max-w-2xl w-full bg-zinc-800 text-white flex rounded-md">
      <section class="w-full flex flex-col gap-3 items-center p-8">
        <header class="my-4">
          <h3 class="text-2xl text-center">Welcome back!</h3>
          <p class="font-extralight">We are very excited to see you here</p>
        </header>

        <article class="flex flex-col w-full">
          <label for="email" class="text-sm pb-2 font-medium">Email or phone  <span class="text-red-700">*</span></label>
          <input id="email" type="text" class="bg-zinc-900 p-2 rounded-sm"/>
        </article>
        <article class="flex flex-col w-full">
          <label for="password"  class="text-sm pb-2 font-medium">Passoword <span class="text-red-700">*</span></label>
          <input id="password" type="text" class="bg-zinc-900 p-2 rounded-sm"/>
          <span class="text-blue-600 underline text-sm mt-2">Forget password?</span>
        </article>

        <footer class="w-full">
          <nuxt-link
          to='/'
            class="w-full flex flex-row gap-2 justify-center items-center rounded-sm mt-4 px-6 font-medium h-10 text-sm bg-blue-500 text-center text-white hover:brightness-95 "
          >Go to home</nuxt-link>
          <p class="text-xs mt-4">Needs a count? <span class="text-blue-500 underline">Sign Up</span></p>
        </footer>
      </section> 

      <section class="hidden p-8 sm:flex sm:flex-col sm:justify-center sm:items-center sm:gap-4">

        <img src="@/static/svg/discord_assets/QR_code.png" class="max-w-xs w-full"/>
        <h4 class="text-lg">Login with QR code</h4>

        <p class="text-sm text-center">Scan this code in your phone to enter automatically</p>
      </section>
    </main>
  </div>
</template>