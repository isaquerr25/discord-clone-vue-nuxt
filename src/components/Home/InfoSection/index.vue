<script setup lang="ts">
import { PropType } from "vue";

import chatImg from "@/static/svg/discord_assets/chat_with_friends.svg";
import takeRest from "@/static/svg/discord_assets/take_a_rest.svg";
import groups from "@/static/svg/discord_assets/discord_groups.svg";

const imageOptions = {
  0: chatImg,
  1: takeRest,
  2: groups,
};

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
  id: {
    type: Number as PropType<keyof typeof imageOptions>,
    required: true,
  },
});
</script>

<template>
  <div class="bg-white w-full section-info">
    <section
      class="flex flex-col py-24 max-w-7xl mx-auto md:flex-row sm:flex-col sm:items-center"
    >
      <article
        class="max-w-lg w-full flex flex-col justify-start items-center p-8 gap-2"
      >
        <h2 class="archivo font-black text-3xl sm:text-4xl sm:text-center">
          {{ props.title }}
        </h2>
        <p class="text-black mt-4 sm:text-center">{{ props.text }}</p>
      </article>

      <aside>
        <img :src="imageOptions[props.id]" />
      </aside>
    </section>
  </div>
</template>
