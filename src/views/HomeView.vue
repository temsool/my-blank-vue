<template>
  <v-app>
    <v-main>
      <HomePage />
    </v-main>
  </v-app>
</template>

<script>
import { defineComponent } from "vue";

// Components
import HomePage from "@/components/HomePage.vue";

export default defineComponent({
  name: "HomeView",

  components: {
    HomePage,
  },
});
</script>
