<template>
  <h1>{{ msg }}</h1>
  <!-- <h1>test</h1> -->
</template>

<script>
  export default {
    name: 'Main',
    props: {
      msg: String,
    },
    // data() {
    //   return {
    //     count: 0,
    //   };
    // },
  };
</script>
<style scoped>
  h1 {
    color: #00c13c;
  }
</style>
