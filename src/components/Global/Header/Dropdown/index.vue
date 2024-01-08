<script setup lang="ts">
import { Icon } from "@iconify/vue2";
import { onMounted, PropType, ref, Ref } from "vue";
import { gsap, Expo } from "gsap";
import { INavLink } from "@/components/Global/Header/index.vue";
import VueRouter from "vue-router";

const isDropdownOpen = ref(false);

const handleDropdown = (mode: "open" | "close") => {
  isDropdownOpen.value = !isDropdownOpen.value;

  gsap.to("#dropdown", {
    x: mode === "open" ? 0 : "100%",
    ease: Expo.easeOut,
  });

  if (mode === "close") return (document.body.style.overflow = "auto");

  return (document.body.style.overflow = "hidden");
};

const props = defineProps({
  links: {
    type: Array as PropType<INavLink[]>,
    required: true,
  },
});

onMounted(() => {
  props.links.forEach(link => {
    if(VueRouter.START_LOCATION.path !== link.path) return;

    const activeLink = document.getElementById(`${link.slug}`);

    activeLink?.classList.add('active')
  })
});
</script>

<template>
  <div>
    <button
      class="w-10 aspect-square grid place-items-center block relative md:hidden"
      @click="handleDropdown('open')"
    >
      <Icon icon="material-symbols:menu" width="30" />
    </button>

    <article
      :v-if="isDropdownOpen"
      class="z-20 bg-white fixed h-full w-80 top-0 right-0 translate-x-80"
      id="dropdown"
    >
      <button
        class="w-10 aspect-square grid place-items-center"
        @click="handleDropdown('close')"
      >
        <Icon icon="material-symbols:menu" width="32" />
      </button>

      <header class="flex justify-between px-8">
        <div class="flex gap-2 items-center">
          <Icon icon="fa6-brands:discord" width="30" color="#000" />
          <p
            class="roboto font-extrabold uppercase tracking-wide text-lg text-black"
          >
            Discord
          </p>
        </div>

        <button @click="handleDropdown('close')">
          <Icon icon="material-symbols:close-rounded" width="32" color="#000" />
        </button>
      </header>
      <nav
        class="flex flex-col gap-4 m-8 border-t-2 border-gray-200 pt-4 text-black"
      >
        <p
          v-for="link in props.links"
          :to="link.path"
          class="nuxt-link"
          id="link.slug"
          >{{ link.slug }}</p
        >
      </nav>
    </article>

    <article
      v-if="isDropdownOpen"
      class="z-10 fixed h-full w-full top-0 right-0 bg-black/[0.4]"
      @click="handleDropdown('close')"
      id="window-dropdown"
    ></article>
  </div>
</template>

<style scoped>
.nuxt-link {
  @apply hover:underline hover:decoration-1 p-2 rounded-sm;
}

.active {
  @apply bg-slate-100 text-blue-700
}
</style>
