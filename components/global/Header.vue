<template>
<div class="fixed z-10 w-full bg-transparent">
  <div class="navbar w-full text-neutral-content rounded-box">
    <!-- Responsive toggle -->
    <div class="flex-none md:hidden lg:hidden xl:hidden 2xl:hidden">
      <button class="btn btn-outline" @click="toggleNav">
        <svg v-if="!isActive" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current">           
          <path fill="black" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>               
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current">   
          <path fill="black" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>                       
        </svg>
      </button>
    </div>

    <div class="px-2 mx-2 navbar-start">
      <!-- <div class="flex-none">
        <div class="avatar">
          <div class="rounded-full w-10 h-10 m-1">
            <img src="https://i.pravatar.cc/500?img=32">
          </div>
        </div>
      </div> -->
    </div> 
    <div class="hidden px-2 mx-2 navbar-center md:flex lg:flex">
      <div class="flex items-stretch">
        <nuxt-link class="btn btn-ghost btn-sm rounded-btn text-black" to="/">Home</nuxt-link>
        <nuxt-link class="btn btn-ghost btn-sm rounded-btn text-black" to="/blog">Blog</nuxt-link>
        <nuxt-link class="btn btn-ghost btn-sm rounded-btn text-black" to="/projects">Projects</nuxt-link>
      </div>
    </div> 
    <div class="navbar-end">
      <!--  -->
    </div>
  </div>
  <!-- Responsive menu -->
  <ul class="menu rounded-box bg-white" v-show="isActive">
    <li>
      <nuxt-link to="/" class="flex justify-center">
        <span class="text-black">
          Home
        </span>
      </nuxt-link>
    </li>
    <li>
      <nuxt-link to="/blog" class="flex justify-center">
        <span class="text-black">
          Blog
        </span>
      </nuxt-link>
    </li>
    <li>
      <nuxt-link to="/projects" class="flex justify-center">
        <span class="text-black">
          Projects
        </span>
      </nuxt-link>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isActive: false
    }
  },
  methods: {
    toggleNav() {
      this.isActive = !this.isActive
    },
    toggleCloseNav() {
      this.isActive = false
    }
  },
}
</script>

<style lang="postcss" scoped>
/* .scrim-bg {
  &::before {
    content: '';
    z-index: -1;
    background-color: var(--bg);
    @apply absolute bottom-0 inset-x-0 h-12 mb-4 transition-colors duration-200 ease-in-out;
  }
  &::after {
    content: '';
    z-index: -1;
    opacity: 1;
    animation: fadeIn1 500ms ease-in-out;
    @apply pointer-events-none absolute bottom-0 inset-x-0 h-16 -mb-12;
    background: linear-gradient(to bottom, #111827, cubic-bezier(0.15, 0, 0.45, 1), transparent);
  }
}
.nuxt-link-exact-active {
  @apply text-gray-200 border-gray-400 bg-gray-800 bg-opacity-25 cursor-default;
}

.light {
  & .scrim-bg {
    &::after {
      animation-name: fadeIn2;
      background: linear-gradient(to bottom, #e5e7eb, cubic-bezier(0.15, 0, 0.45, 1), transparent);
    }
  }
  & .nuxt-link-exact-active {
    @apply text-primary-700 border-gray-600 bg-gray-100;
  }
} */

/* Need two because of smoother switching between color modes */
@keyframes fadeIn1 {
  from { opacity: 0; }
  to { opacity: 1; }
}
@keyframes fadeIn2 {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>
