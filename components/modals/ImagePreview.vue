<template>
  <modal name="modals-image-preview" :adaptive="true" :minHeight="600">
    <img class="w-full" :src="post.file" />
    <div class="p-8">
      <div class="text-lg">
        <b>Title:</b> {{ post.title }}
        <span class="float-right"><HeartIcon :fill="post.is_liked" /> </span>
      </div>
      <p><b>Description: </b>{{ post.description }}</p>
      <p><b>Author: </b>{{ post?.user?.name }}</p>
      <p><b>Total Likes: </b>{{ post.totalLikes }}</p>
    </div>
  </modal>
</template>

<script>
export default {
  name: "ModalsImagePreview",

  props: {
    post: {
      type: Object,
      default: {},
    },
  },
};
</script>
