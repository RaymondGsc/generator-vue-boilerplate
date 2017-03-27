<template>
  <div class="logo">
    <img :src="logo" alt="logo" />
  </div>
</template>

<script>
const logo = require('@/assets/images/logo.png')

export default {
  name: 'logo',
  data() {
    return {
      logo,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.logo {
  width: 200px;
}
</style>
