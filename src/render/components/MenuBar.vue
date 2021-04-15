<template>
  <section class="menuBar">
    <el-header class="header">
      <router-link to="/">
        <el-button
          style="justify-content: left"
          class="btn-small"
          type="text"
          icon="el-icon-arrow-left"
        >
          {{ buttonText }}
        </el-button>
      </router-link>
    </el-header>
  </section>
</template>

<script>
  export default {
    name: 'MenuBar',
    data() {
      return {
        buttonText: 'menu',
      };
    },
  };
</script>

<style scoped>
  .menuBar {
    padding: 0;
    margin: 0;
  }
</style>
