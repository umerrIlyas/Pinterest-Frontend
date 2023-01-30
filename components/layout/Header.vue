<template>
  <nav class="bg-white border-gray-200 px-2 sm:px-4 border-b-2 shadow-md">
    <div class="container flex flex-wrap items-center justify-between mx-auto">
      <NuxtLink to="/" class="flex items-center">
        <span
          class="self-center text-4xl font-bold whitespace-nowrap dark:text-dark"
        >
          Pinterest App
        </span>
      </NuxtLink>

      <div class="w-full md:block md:w-auto" id="navbar-default">
        <ul
          class="flex flex-col p-4 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white"
        >
          <li>
            <NuxtLink to="/posts/favorite">
              <Button
                :text="'Favorite'"
                :heartIcon="true"
                :additionalClasses="[
                  'flex text-black hover:text-white hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-md text-sm py-2  px-16 border  dark:focus:ring-gray-700 dark:border-gray-700',
                ]"
                :fullWidth="true"
              />
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/posts/upload">
              <Button
                :text="'Upload'"
                :additionalClasses="[
                  'text-white bg-gray-400 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-md text-sm py-2.5 dark:bg-gray-500 px-20 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
                ]"
                :fullWidth="true"
              />
            </NuxtLink>
          </li>
          <li v-if="!$auth.loggedIn">
            <NuxtLink to="/auth/login">
              <Button
                :text="'Login'"
                :additionalClasses="[
                  'text-white bg-gray-500 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-md text-sm py-2.5 dark:bg-gray-700 px-20 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
                ]"
                :fullWidth="true"
              />
            </NuxtLink>
          </li>
          <li v-else>
            <Button
              @onClick="onClick"
              :text="'Logout'"
              :additionalClasses="[
                'text-white bg-gray-500 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-md text-sm py-2.5 dark:bg-gray-700 px-20 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700',
              ]"
              :fullWidth="true"
            />
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "LayoutHeader",

  methods: {
    async onClick() {
      await this.$auth.logout();
      this.$toast.success("Logged out.");
    },
  },
};
</script>
