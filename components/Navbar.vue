<template>
  <header
    class="flex bg-white border-b py-4 sm:px-8 px-6 font-[sans-serif] min-h-[80px] tracking-wide relative z-50"
  >
    <div class="flex flex-wrap items-center lg:gap-y-2 gap-4 w-full">
      <NuxtLink href="/">
        <img
          src="/logo1.svg"
          alt="logo"
          class="w-16 lg:w-24"
        />
      </NuxtLink>

      <div
        :class="['lg:ml-10', { 'max-lg:block': isMenuOpen, 'max-lg:hidden': !isMenuOpen }]"
        id="collapseMenu"
      >
        <button
          id="toggleClose"
          class="lg:hidden fixed top-2 right-4 z-[100] rounded-full bg-white p-3"
          @click="toggleMenu"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-4 fill-black"
            viewBox="0 0 320.591 320.591"
          >
            <path
              d="M30.391 318.583a30.37 30.37 0 0 1-21.56-7.288c-11.774-11.844-11.774-30.973 0-42.817L266.643 10.665c12.246-11.459 31.462-10.822 42.921 1.424 10.362 11.074 10.966 28.095 1.414 39.875L51.647 311.295a30.366 30.366 0 0 1-21.256 7.288z"
              data-original="#000000"
            ></path>
            <path
              d="M287.9 318.583a30.37 30.37 0 0 1-21.257-8.806L8.83 51.963C-2.078 39.225-.595 20.055 12.143 9.146c11.369-9.736 28.136-9.736 39.504 0l259.331 257.813c12.243 11.462 12.876 30.679 1.414 42.922-.456.487-.927.958-1.414 1.414a30.368 30.368 0 0 1-23.078 7.288z"
              data-original="#000000"
            ></path>
          </svg>
        </button>

        <ul
          class="lg:flex lg:gap-x-3 max-lg:space-y-3 max-lg:fixed max-lg:bg-white max-lg:w-1/2 max-lg:min-w-[300px] max-lg:top-0 max-lg:left-0 max-lg:p-6 max-lg:h-full max-lg:shadow-md max-lg:overflow-auto z-50"
        >
          <li class="mb-6 hidden max-lg:block">
            <NuxtLink href="/">
              <img
                src="/logo1.svg"
                lazy="loading"
                alt="logo"
                class="w-16 lg:w-24"
              />
            </NuxtLink>
          </li>
          <li class="max-lg:border-b max-lg:py-3 px-3">
            <NuxtLink
              href="/"
              class="text-[#007bff] hover:text-[#007bff] text-[15px] block font-semibold"
              >Home</NuxtLink
            >
          </li>
          <li class="max-lg:border-b max-lg:py-3 px-3">
            <NuxtLink
              href="/Contact"
              class="text-[#333] hover:text-[#007bff] text-[15px] block font-semibold"
              >Contact</NuxtLink
            >
          </li>
        </ul>
      </div>

      <div class="flex gap-x-6 gap-y-4 ml-auto">
        <div
          class="flex border-2 focus-within:border-gray-400 rounded-full px-6 py-3 overflow-hidden max-w-52 max-lg:hidden"
        >
          <input
            v-model="searchTerm"
            @input="updateSearchTerm"
            type="text"
            placeholder="Search for shoes..."
            class="border border-gray-300 rounded-md p-2 w-full max-w-md"
          />
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 192.904 192.904"
            width="16px"
            class="cursor-pointer fill-gray-600"
          >
            <path
              d="m190.707 180.101-47.078-47.077c11.702-14.072 18.752-32.142 18.752-51.831C162.381 36.423 125.959 0 81.191 0 36.422 0 0 36.423 0 81.193c0 44.767 36.422 81.187 81.191 81.187 19.688 0 37.759-7.049 51.831-18.751l47.079 47.078a7.474 7.474 0 0 0 5.303 2.197 7.498 7.498 0 0 0 5.303-12.803zM15 81.193C15 44.694 44.693 15 81.191 15c36.497 0 66.189 29.694 66.189 66.193 0 36.496-29.692 66.187-66.189 66.187C44.693 147.38 15 117.689 15 81.193z"
            ></path>
          </svg>
        </div>

        <div class="flex items-center space-x-8">
          <span class="relative">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20px"
              class="cursor-pointer fill-[#333] inline"
              viewBox="0 0 64 64"
            >
              <path
                d="M45.5 4A18.53 18.53 0 0 0 32 9.86 18.5 18.5 0 0 0 0 22.5C0 40.92 29.71 59 31 59.71a2 2 0 0 0 2.06 0C34.29 59 64 40.92 64 22.5A18.52 18.52 0 0 0 45.5 4ZM32 55.64C26.83 52.34 4 36.92 4 22.5a14.5 14.5 0 0 1 26.36-8.33 2 2 0 0 0 3.27 0A14.5 14.5 0 0 1 60 22.5c0 14.41-22.83 29.83-28 33.14Z"
                data-original="#000000"
              />
            </svg>
            <span
              class="absolute left-auto -ml-1 top-0 rounded-full bg-red-500 px-1 py-0 text-xs text-white"
              >0</span
            >
          </span>

          <span class="relative">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20px"
              height="20px"
              class="cursor-pointer fill-[#333] inline"
              viewBox="0 0 512 512"
            >
              <path
                d="M164.96 300.004h.024c.02 0 .04-.004.059-.004H437a15.003 15.003 0 0 0 14.422-10.879l60-210a15.003 15.003 0 0 0-2.708-13.284A15 15 0 0 0 497 60.004H141.676L126.12 2.4A15 15 0 0 0 111.682-9.4H15C6.716-9.4 0 6.316 0 14.6S6.716 32.6 15 32.6h81.02l15.555 57.604.024.09 39.58 146.672-24.898 38.796a14.999 14.999 0 0 0 12.679 23.142Zm269.38-210h-92.796l-14.737 30H420.96l-14.737 30h-92.796l-14.737 30H404.96l-14.737 30H297.426l-14.737 30H388.96l-14.737 30H273.926l-14.737 30H372.96l-14.737 30H250.426l-14.737 30h92.776L313.664 372H233.526L173.25 179.624l-8.82-32.688h330.265l-42 150zM82.08 472c0 22.056 17.944 40 40 40s40-17.944 40-40-17.944-40-40-40-40 17.944-40 40zm260 0c0 22.056 17.944 40 40 40s40-17.944 40-40-17.944-40-40-40-40 17.944-40 40z"
                data-original="#000000"
              ></path>
            </svg>
            <span
              class="absolute left-auto -ml-1 top-0 rounded-full bg-red-500 px-1 py-0 text-xs text-white"
              >0</span
            >
          </span>

          <button
            class="lg:hidden inline-flex justify-center items-center group"
            @click="toggleMenu"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
              class="w-6 h-6"
            >
              <path
                fill-rule="evenodd"
                d="M2.75 5a.75.75 0 0 1 .75-.75h13.5a.75.75 0 0 1 0 1.5H3.5A.75.75 0 0 1 2.75 5zM2.75 10a.75.75 0 0 1 .75-.75h13.5a.75.75 0 0 1 0 1.5H3.5a.75.75 0 0 1-.75-.75zM3.5 14.25a.75.75 0 0 0 0 1.5h13.5a.75.75 0 0 0 0-1.5H3.5z"
                clip-rule="evenodd"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: '',
      isMenuOpen: false // Example state for menu toggle
    };
  },
  methods: {
    updateSearchTerm() {
      this.$emit('update:searchTerm', this.searchTerm);
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    }
  }
};
</script>
