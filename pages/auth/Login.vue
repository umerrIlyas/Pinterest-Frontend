<template>
  <div>
    <h1 class="uppercase text-center text-4xl font-bold mt-10">Login</h1>

    <form class="md:w-3/12 mt-24 mx-auto" @submit.prevent="login">
      <div class="grid grid-flow-col mb-8">
        <NuxtLink to="/auth/Login">
          <Button
            :text="'Login'"
            :additionalClasses="[
              'text-white grid-cols-6 w-full  bg-gray-400 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-sm py-3    dark:bg-gray-500 px-auto dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
            ]"
            :fullWidth="true"
          />
        </NuxtLink>
        <NuxtLink to="/auth/signup">
          <Button
            :text="'Sign up'"
            :additionalClasses="[
              ' grid-cols-6 w-full text-black hover:text-white hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-sm  py-3 border  dark:focus:ring-gray-700 dark:border-gray-700',
            ]"
            :fullWidth="true"
          />
        </NuxtLink>
      </div>

      <Input :text="'Email'" :placeholder="'Your email'" v-model="email" />

      <Input
        :type="'password'"
        :text="'password'"
        :placeholder="'password'"
        v-model="password"
      />

      <Button
        :type="'submit'"
        :text="'Login'"
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
      email: "",
      password: "",
    };
  },

  methods: {
    login() {
      if (this.email && this.password) {
        this.$auth.loginWith("laravelSanctum", {
          data: {
            email: this.email,
            password: this.password,
          },
        });
        this.$toast.success("Login successfully.");
      } else {
        this.$toast.error("Not all amendatory filled.");
      }
    },
  },
};
</script>
