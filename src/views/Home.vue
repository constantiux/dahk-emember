<template>
  <div v-if="!isAuthenticated && !isLoading">
    <hero />
    <hr />
    <home-content />
  </div>
  <div v-if="isAuthenticated" class="text-center hero">
    <img class="mb-3 app-logo" src="/app-logo.png" alt="Vue.js logo" width="120" />
    <h1 class="mb-4">Hello, {{ user.name }}</h1>
    <p class="lead">
      You are now logged in.
    </p>
  </div>
</template>

<script lang="ts">
import Hero from "../components/Hero.vue";
import HomeContent from "../components/HomeContent.vue";
import { useAuth0 } from '@auth0/auth0-vue';

export default {
  name: "home-view",
  components: {
    Hero,
    HomeContent,
  },
  setup() {
    const auth0 = useAuth0();
    
    return {
      isAuthenticated: auth0.isAuthenticated,
      isLoading: auth0.isLoading,
      user: auth0.user,
    }
  }
};
</script>

<style lang="css" scoped>
.next-steps .fa-link {
    margin-right: 5px;
}
</style>
