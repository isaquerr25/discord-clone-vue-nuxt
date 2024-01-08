<script lang="ts" setup>
import { gsap } from "gsap";
import { onMounted, ref } from "vue";
import { Icon } from "@iconify/vue2";

import Background from "@/components/Home/Background/index.vue";
import Header from "@/components/Global/Header/index.vue";
import InfoSection from "@/components/Home/InfoSection/index.vue";
import Footer from "@/components/Global/Footer/index.vue";

import InfoSectionsJSON from "@/data/homeSections.json";
const infoSectionsArr = ref(InfoSectionsJSON.info);

onMounted(() => {
  const getIntroStatus = window.sessionStorage.getItem("@HAS_INTRO_CLONE");

  if (getIntroStatus) {
    gsap.to("#home-view", { opacity: 1, delay: 1, duration: 0.8 });
  } else {
    gsap.to("#home-view", { opacity: 1, delay: 13, duration: 0.8 });
  }
});
</script>

<template>
  <div>
    <div id="home-view" class="opacity-0 bg-blue-600">
      <div class="relative h-full">
        <Header />
        <Background />
        <main
          class="z-10 layout max-w-7xl mx-auto grid place-items-center m-b-4"
        >
          <section
            class="max-w-2xl w-full flex flex-col sm:items-center text-white px-4 py-2 gap-4"
          >
            <header>
              <h1
                class="archivo font-black text-4xl sm:text-5xl sm:text-center md:text-7xl"
              >
                IMAGINE A PLACE...
              </h1>
            </header>

            <section>
              <p class="font-medium sm:text-lg sm:text-center">
                ...where you can belong to a school club, a group of gamers, or
                a global artistic community. Where you and some friends can
                spend time together. A place that makes it easy to chat every
                day and socialize more often.
              </p>
            </section>

            <footer class="flex items-center gap-4 pt-4 sm:flex-row">
              <button class="btn bg-white text-gray-900">
                <Icon
                  icon="material-symbols:download-rounded"
                  height="30"
                  width="30"
                />
                Download for windows
              </button>

              <button class="btn bg-gray-900">Open Discord on browser</button>
            </footer>
          </section>

          <img
            class="sm:hidden"
            src="@/static/svg/discord_assets/hang_out.svg"
          />
        </main>

        <section class="layout">
          <ul>
            <InfoSection v-for="item in infoSectionsArr" v-bind="item" />
          </ul>
        </section>

        <section class="layout">
          <article
            class="section-info bg-gray-100 px-8 py-32 flex flex-col items-center"
          >
            <h2 class="archivo font-black text-4xl sm:text-center">
              RELIABLE CONNECTION TECHNOLOGY
            </h2>
            <p class="max-w-4xl mt-8">
              Low-latency voice and video for you to chat as if you were in the
              same room. Give a thumbs-up on video, watch friends streaming
              their gameplay of the day, or gather a group to draw on the shared
              screen.
            </p>

            <img
              class="w-9/12 max-w-4xl"
              src="@/static/svg/discord_assets/network_safety.svg"
            />
          </article>
        </section>

        <section class="">
          <article
            class="relative section-info bg-gray-100 p-4 pb-32 flex flex-col items-center"
          >
            <h2 class="archivo font-black text-3xl text-center sm:text-4xl">
              Shall we start your journey?
            </h2>

            <img
              class="-translate-y-24"
              src="@/static/svg/discord_assets/stars.svg"
            />

            <button class="max-w-xs btn bg-blue-700 text-white">
              <Icon
                icon="material-symbols:download-rounded"
                height="30"
                width="30"
              />
              Download for windows
            </button>
          </article>
        </section>
      </div>

      <Footer />
    </div>
  </div>
</template>

<style>
.btn {
  @apply flex flex-row gap-2 items-center justify-center rounded-full px-6 font-medium h-12 text-sm sm:h-14 cursor-pointer;
}

.section-info:nth-child(even) {
  @apply bg-gray-100;
}

.section-info:nth-child(odd) > section {
  @apply md:flex-row-reverse;
}
</style>
