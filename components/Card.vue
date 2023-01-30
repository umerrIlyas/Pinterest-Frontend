<template>
  <div>
    <div class="my-4">
      <div class="max-w-sm rounded overflow-hidden shadow-lg">
        <img
          class="w-full"
          @click="handle"
          :src="post.file"
          :alt="post.title"
        />
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">{{ post.title }}</div>
          <p class="text-gray-700 text-base">
            {{ post.description }}
          </p>
        </div>
        <div class="px-6 pb-6">
          <span class="text-xs">
            <b>Author: </b> {{ post.user.name }} <br />
            <b> Total Likes: </b>{{ post.totalLikes }}
          </span>

          <HeartIcon :fill="post.is_liked" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "Card",

  props: {
    post: {
      type: Object,
      default: {},
    },
  },

  methods: {
    ...mapActions({
      setPost: "posts/setPost",
    }),
    handle() {
      this.setPost(this.post);
      this.$modal.show("modals-image-preview");
    },
  },
};
</script>
