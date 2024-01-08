<script setup lang="ts">
import { onMounted, Ref, ref } from "vue";
import { Icon } from "@iconify/vue2";
import FooterLinksJSON from "@/data/footerLinks.json";

type ILink = {
  group: keyof IGroups;
  links: {
    name: string;
    path: string;
  }[];
};

type IGroups = "Product" | "Enterprise" | "Resources" | "Policy";

type ISocialLinks = {
  path: string;
  icon: string;
};
const footerLinks: Ref<ILink[]> = ref(FooterLinksJSON);

const socialLinks: Ref<ISocialLinks[]> = ref([
  {
    path: "https://twitter.com/discord",
    icon: "mdi:twitter",
  },
  {
    path: "https://www.instagram.com/discord/",
    icon: "mdi:instagram",
  },
  {
    path: "https://www.facebook.com/discord/",
    icon: "mdi:facebook",
  },
  {
    path: "https://www.youtube.com/discord/",
    icon: "mdi:youtube",
  },
]);
</script>

<template>
  <div class="bg-neutral-800">
    <footer class="max-w-7xl mx-auto flex flex-col">
      <div
        class="flex flex-col justify-between-4 py-16 md:pb-0 md:flex-row sm:flex-col"
      >
        <article class="w-96 flex flex-col gap-4 p-4 pt-0">
          <h3 class="uppercase archivo font-black text-4xl text-blue-600">
            Imagine a <br />place
          </h3>

          <div class="flex gap-2 text-white items-center">
            <Icon icon="emojione-v1:flag-for-united-states" height="20" />
            <p class="font-light">United States</p>
          </div>

          <nav class="flex gap-4 text-gray-200">
            <a
              v-for="socialLink in socialLinks"
              :href="socialLink.path"
              target="_blank"
            >
              <Icon :icon="socialLink.icon" height="30" />
            </a>
          </nav>
        </article>

        <section class="grid-style gap-8 p-4">
          <article class="px-2" v-for="groupObj in footerLinks">
            <span class="text-blue-600 text-lg font-medium">{{
              groupObj.group
            }}</span>
            <ul class="mt-2 flex flex-col gap-1">
              <nuxt-link
                v-for="links in groupObj.links"
                :to="links.path"
                :key="links.name"
                class="text-gray-300 hover:underline hover:decoration-1 text-ellipsis"
                >{{ links.name }}</nuxt-link
              >
            </ul>
          </article>
        </section>
      </div>

      <aside
        class="flex m:4 p-4 justify-between border-t-2 pt-6 pb-6 border-blue-600 sm:m-2 sm:py-4 sm:px-0"
      >
        <div class="flex gap-2 items-center">
          <Icon icon="fa6-brands:discord" width="30" color="#fff" />
          <p
            class="roboto font-extrabold uppercase tracking-wide text-lg text-white"
          >
            Discord
          </p>
        </div>
        <button
          class="flex flex-row gap-2 items-center rounded-full px-6 font-medium h-10 text-sm bg-blue-600 text-white"
        >
          Registry
          <Icon
            icon="material-symbols:download-rounded"
            height="20"
            width="20"
          />
        </button>
      </aside>
    </footer>
  </div>
</template>

<style scoped>
.grid-style {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

@media (min-width: 820px) {
  .grid-style {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (min-width: 1000px) {
  .grid-style {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
