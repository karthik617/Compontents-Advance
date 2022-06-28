<template>
<the-header title="RememberMe"></the-header>
<the-resourse></the-resourse>
</template>

<script>

import TheHeader from './components/layout/TheHeader.vue';
import TheResourse from './components/TheResourse.vue';

export default {
  components: { TheHeader ,TheResourse},
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
