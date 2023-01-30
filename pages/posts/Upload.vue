<template>
  <div>
    <h1 class="uppercase text-center text-4xl font-bold mt-10">
      Upload your Image
    </h1>

    <form class="md:w-3/12 mt-24 mx-auto" @submit.prevent="onSubmit">
      <Input
        :text="'Upload Image'"
        :type="'file'"
        :placeholder="'Choose File'"
        :required="true"
        v-model="file"
      />

      <Input
        :text="'title'"
        :placeholder="'Image Title'"
        :required="true"
        v-model="title"
      />

      <Input
        :text="'description'"
        :placeholder="'Image Description'"
        :required="true"
        v-model="description"
      />

      <Button
        :type="'submit'"
        :text="'Upload'"
        :additionalClasses="[
          'w-full text-white flex justify-center bg-gray-500 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-full text-sm py-6 mt-2 dark:bg-gray-700 px-20 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
        ]"
      />
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      description: "",
      file: "",
    };
  },

  methods: {
    onSubmit() {
      if (this.title && this.title && this.file) {
        if (this.$auth.loggedIn) {
          let formData = new FormData();
          formData.append("file", this.file);
          formData.append("title", this.title);
          formData.append("description", this.description);

          this.$axios
            .post("/posts", formData, {
              headers: {
                "Content-Type": "multipart/form-data",
              },
            })
            .then((response) => {
              console.log(response);
              this.$toast.success(response.data.message);
            })
            .catch((error) => {
              console.log(error);
              this.$toast.error(error.response.data.message);
            });
        } else {
          this.$toast.error("Login First.");
        }
      } else {
        this.$toast.error("Not all amendatory filled.");
      }
    },
  },
};
</script>
