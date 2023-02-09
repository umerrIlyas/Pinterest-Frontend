<template>
  <div class="container mx-auto">
    <h1 class="m-auto text-center my-5 text-3xl font-semibold">
      Favorite Posts
    </h1>

    <Grid :posts="posts" :loading="loading" />

    <div class="flex justify-center my-20">
      <Button
        @onClick="getMorePosts"
        :text="'load more'"
        :additionalClasses="[
          'm-auto text-white flex justify-center bg-gray-500 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-full text-sm py-2.5 dark:bg-gray-700 px-20 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
        ]"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Favorite",

  data() {
    return {
      posts: [],
      postData: {},
      loading: false,
    };
  },

  mounted() {
    // if (this.$auth.loggedIn) this.getFavoritePosts();
    // else this.$toast.error("Login First");
  },

  methods: {
    getFavoritePosts() {
      this.loading = true;
      this.$axios
        .get("/favorites")
        .then((response) => {
          this.posts = response.data.posts.data;
          this.postData = response.data.posts;
          this.loading = false;
        })
        .catch((error) => {
          this.loading = false;
          this.$toast.error(error);
        });
    },

    getMoreFavoritePosts() {
      this.loading = true;
      this.$axios
        .get(`/favorites?page=${this.postData.meta.current_page + 1}`)
        .then((response) => {
          this.postData = response.data.posts;
          this.posts.push(...response.data.posts.data);
          this.loading = false;
        })
        .catch((error) => {
          this.loading = false;
          this.$toast.error(error);
        });
    },
  },
};
</script>
