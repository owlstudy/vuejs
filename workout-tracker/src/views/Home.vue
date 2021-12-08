<template>
  <div v-if="dataLoaded" class="container mt-10 px-4">
    <div v-if="data.length === 0" class="w-full flex flex-col items-center">
      <h1 class="text-2xl">Looks empty here...</h1>
      <!-- <router-link :to="{ name: 'Create' }"> Create Workout </router-link> -->
    </div>
  </div>
</template>

<script>
import { ref } from "vue"
import { supabase } from "../supabase/init"
export default {
  name: "home",
  components: {},
  setup() {
    // Create data / vars
    const data = ref([])
    const dataLoaded = ref(null)
    // Get data
    const getData = async () => {
      try {
        const { data: workouts, error } = await supabase
          .from("workouts")
          .select("*")
        // console.log(data)
        if (error) throw error
        data.value = workouts
        dataLoaded.value = true
        console.log(data.value, "data value")
      } catch (error) {
        console.warn(error.message)
      }
    }

    // Run data function
    getData()
    return { data, dataLoaded }
  },
}
</script>
