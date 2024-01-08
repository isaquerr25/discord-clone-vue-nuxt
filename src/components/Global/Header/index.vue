<script setup lang="ts">
import { Icon } from "@iconify/vue2";
import { computed, onMounted, Ref, ref } from "vue";
import NavLinks from "@/data/navLinks.json";
import Dropdown from "@/components/Global/Header/Dropdown/index.vue";

export type INavLink = { slug: String; path: string };

const navLinks: Ref<INavLink[]> = ref(NavLinks.links);

const randomId = computed(() => Math.random().toString(36).substring(2, 9));
</script>

<template>
  <section>
    <header class="m-auto max-w-7xl p-4 text-white flex items-center gap-4">
      <article class="flex gap-2 items-center">
        <Icon icon="fa6-brands:discord" width="40" color="#fff" />
        <p class="roboto font-extrabold tracking-wide text-lg">DISCORD</p>
      </article>

      <nav
        class="flex-auto text-sm hidden sm:gap-2 md:flex md:justify-center md:gap-8 md:text-md"
      >
        <nuxt-link
          v-for="link in navLinks.slice(1,navLinks.length)"
          :key="randomId + link"
          :to="link.path"
          class="font-semibold hover:underline hover:decoration-1"
          >{{ link.slug }}</nuxt-link
        >
      </nav>

      <aside class="ml-auto">
        <nuxt-link
        to="/login"
          class="bg-white transition-colors duration-200 text-slate-950 py-2 px-4 text-sm rounded-full hover:shadow-lg hover:text-blue-700"
        >
          Login
        </nuxt-link>
      </aside>

      <Dropdown :links="navLinks" />
    </header>
  </section>
</template>
