<template>
  <header class="bg-at-light-green text-white">
    <nav
      class="container py-5 px-4 flex flex-col gapp-4 items-center sm:flex-row"
    >
      <div class="flex items-center gap-x-4">
        <img class="w-14" src="../assets/images/dumbbell-light.png" alt="" />
        <h1 class="text-lg">Active Tracker</h1>
      </div>
      <ul></ul>
    </nav>
  </header>
  <!-- <header class="bg-at-light-green text-white">
    <nav
      class="container py-5 px-4 flex flex-col gap-4 items-center sm:flex-row"
    >
      <div class="flex items-center gap-x-4">
        <img class="w-14" src="../assets/images/dumbbell-light.png" alt="" />
        <h1 class="text-lg">Active Tracker</h1>
      </div>
      <ul class="flex">
        <router-link>Home</router-link>
        <router-link>Create</router-link>
        <router-link>Login</router-link>
        <li>Logout</li>
      </ul>
    </nav>
  </header> -->
</template>

<script>
import { useRouter } from "vue-router"

export default {
  setup() {
    // Get user from store

    // Setup ref to router
    const router = useRouter()
    // Logout function
    const logout = async () => {
      router.push({ name: "Home" })
    }
    return { logout }
  },
}
</script>
