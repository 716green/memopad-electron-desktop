<template>
  <div class="logo-box">
    <img class="img" src="../assets/memopad.svg" />
    <!-- <svg
      data-v-45502113=""
      version="1.1"
      id="Layer_1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      x="500px"
      y="0px"
      viewBox="0 0 1024 1024"
      xml:space="preserve"
    >
      <g data-v-45502113="" fill="currentColor">
        <polygon
          data-v-45502113=""
          id="Fill-1"
          points="0,265 285.3,992.6 316.9,193.8 	"
          class="st0"
        ></polygon>
        <polygon
          data-v-45502113=""
          id="Fill-2"
          points="389.3,180.1 295.3,993.7 1024,30.3 	"
          class="st0"
        ></polygon>
      </g>
    </svg> -->
  </div>
  <Main msg="Memopad" />
  <router-link to="/create">
    <!-- New -->
    <el-button class="btn success" to="/create">New</el-button>
  </router-link>
  <br />
  <br />
  <el-button class="btn" @click="toggleSettings">Settings</el-button>
  <div class="settings" v-if="settings">
    <h2>Settings</h2>
  </div>
</template>

<script>
  import Main from '../components/Main.vue';
  // const version = require('process').versions.electron;
  export default {
    name: 'Index',
    data() {
      return {
        settings: false,
      };
    },
    methods: {
      toggleSettings() {
        this.settings = !this.settings;
      },
    },
    components: {
      Main,
    },
  };
</script>

<style scoped>
  button {
    background-color: white;
  }

  .btn {
    width: 100%;
  }
  .img {
    width: 200px;
  }

  /* .logo-box {
    width: 20%;
    margin-left: 130px;
  } */
  .success {
    background: #00c13c;
    border: none;
    padding: 10px 80px;
    color: #fff;
    text-decoration: none;
  }
</style>
