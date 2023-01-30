<template>
  <div>
    <ModalsImagePreview :post="post" />
    <div class="xl:columns-7 lg:columns-5 md:columns-5 sm:columns-3 columns-xs">
      <Card v-for="post in posts" :key="post.id" :post="post" />
    </div>
    <div v-if="loading" class="text-center m-auto">
      <Loader />
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "Grid",
  props: {
    posts: {
      type: Array,
      default: [],
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },

  computed: {
    ...mapState("posts", ["post"]),
  },
  methods: {
    openModel() {
      this.$modal.show("modals-image-preview");
    },
  },
};
</script>
