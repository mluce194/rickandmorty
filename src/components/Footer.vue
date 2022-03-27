<template>
  <footer class="bg-[#99cae9] mt-10">
    <div class="p-8 my-auto">
      <p class="text-gray-600 text-xl text-center">{{ texte }}</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterBlock",
  props: {
    texte: String,
  },
};
</script>
