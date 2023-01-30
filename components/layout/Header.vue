<template>
  <nav class="bg-white border-gray-200 px-2 sm:px-4 border-b-2 shadow-md">
    <div class="container flex flex-wrap items-center justify-between mx-auto">
      <NuxtLink to="/" class="flex items-center">
        <span
          class="self-center text-xl text-4xl font-bold whitespace-nowrap dark:text-dark"
        >
          Pinterest App
        </span>
      </NuxtLink>
      <button
        data-collapse-toggle="navbar-default"
        type="button"
        class="inline-flex items-center p-2 ml-3 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
        aria-controls="navbar-default"
        aria-expanded="true"
      >
        <span class="sr-only">Open main menu</span>
        <svg
          class="w-6 h-6"
          aria-hidden="true"
          fill="currentColor"
          viewBox="0 0 20 20"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
            clip-rule="evenodd"
          ></path>
        </svg>
      </button>
      <div class="hidden w-full md:block md:w-auto" id="navbar-default">
        <ul
          class="flex flex-col p-4 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white"
        >
          <li>
            <Button
              :text="'Favorite'"
              :heartIcon="true"
              :additionalClasses="[
                'flex text-black hover:text-white hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-md text-sm py-2  px-16 border  dark:focus:ring-gray-700 dark:border-gray-700',
              ]"
              :fullWidth="true"
            />
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
          <li>
            <Button
              :text="'Login'"
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
};
</script>
