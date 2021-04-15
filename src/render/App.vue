<template>
  <div class="app">
    <section>
      <MenuBar v-if="this.$route.path != '/'" />
      <router-view></router-view>
    </section>
  </div>
</template>

<script lang="ts">
  import MenuBar from './components/MenuBar.vue';
  import { useRouter } from 'vue-router';
  export default {
    components: {
      MenuBar,
    },
    name: 'app',
    setup() {
      const router = useRouter();
      router.push('/');
    },
  };
</script>
<style>
  /* .app {
    
  } */
</style>
