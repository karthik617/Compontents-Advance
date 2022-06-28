<template>
  <ul>
    <list-resourse
      v-for="sr in resourses"
      :key="sr.id"
      :title="sr.title"
      :description="sr.description"
      :link="sr.link"
      :id="sr.id"
    ></list-resourse>
  </ul>
</template>

<script>
import ListResourse from './ListResourse.vue';
export default {
  inject: ['resourses'],
  components: {
    ListResourse,
  },

};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
