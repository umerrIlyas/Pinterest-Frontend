<template>
  <div class="my-4">
    <div class="max-w-sm rounded overflow-hidden shadow-lg">
      <img class="w-full" :src="post.file" :alt="post.title" />
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">{{ post.title }}</div>
        <p class="text-gray-700 text-base">
          {{ post.description }}
        </p>
      </div>
      <div class="px-4 pb-6">
        <HeartIcon :fill="false" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",

  props: {
    post: {
      type: Object,
      default: {},
    },
  },
};
</script>
