<template>
  <div>
    <h1 class="uppercase text-center text-4xl font-bold mt-10">Sign Up</h1>

    <form class="md:w-3/12 mt-24 mx-auto" @submit.prevent="onSubmit">
      <div class="grid grid-flow-col mb-8">
        <NuxtLink to="/auth/Login">
          <Button
            :text="'Login'"
            :additionalClasses="[
              'grid-cols-6 w-full text-black hover:text-white hover:bg-gray-900 focus:outline-none  font-medium rounded-sm  py-3 border  dark:focus:ring-gray-700 dark:border-gray-700',
            ]"
            :fullWidth="true"
          />
        </NuxtLink>
        <NuxtLink to="/auth/signup">
          <Button
            :text="'Sign'"
            :additionalClasses="[
              'text-white grid-cols-6 w-full  bg-gray-400 hover:bg-gray-900 focus:outline-none  font-medium rounded-sm py-3    dark:bg-gray-500 px-auto dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
            ]"
            :fullWidth="true"
          />
        </NuxtLink>
      </div>

      <Input
        :text="'Email'"
        :placeholder="'Your email'"
        :required="true"
        v-model="form.email"
      />

      <Input
        :type="'password'"
        :text="'password'"
        :placeholder="'password'"
        :required="true"
        v-model="form.password"
      />

      <Input
        :type="'password'"
        :text="'repeat password'"
        :placeholder="'password'"
        :required="true"
        v-model="form.confirmPassword"
      />

      <Button
        :type="'submit'"
        :text="'Sign up'"
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
      form: {
        email: "",
        password: "",
        confirmPassword: "",
      },
    };
  },

  methods: {
    onSubmit() {
      if (this.form.email && this.form.password && this.form.confirmPassword) {
        this.$axios
          .post("/auth/login", this.form)
          .then((response) => {
            console.log(response);
            this.$toast.success(response.data.message);
          })
          .catch((error) => {
            console.log(error);
            this.$toast.error(error.response.data.message);
          });
      } else {
        this.$toast.error("Not all amendatory filled.");
      }
    },
  },
};
</script>
