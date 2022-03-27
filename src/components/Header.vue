<template>
  <header class="bg-[#99cae9]">
    <div class="md:flex justify-center py-16">
      <div class="p-2 my-auto">
        <img
          class="rounded-full h-72 w-72 mx-auto border-8 border-white"
          :src="`${image}`"
          :alt="`${imageDescription}`"
        />
      </div>
      <div class="p-8 my-auto">
        <h1 class="text-white text-3xl text-center">{{ title1 }}</h1>
        <p class="text-gray-600 text-xl text-center">{{ title2 }}</p>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderBlock",
  props: {
    title1: String,
    title2: String,
    image: String,
    imageDescription: String,
  },
};
</script>
