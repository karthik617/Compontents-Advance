<template>
  <base-card>
    <base-button
      @click="setSeletedTab('stored-resourse')"
      :mode="storedResoursesMode"
      >Stored Resourse</base-button
    >
    <base-button @click="setSeletedTab('add-resourse')" :mode="addResoursesMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="seletedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResourse from './StoredResourse.vue';
import AddResourse from './AddResourse.vue';
export default {
  components: {
    StoredResourse,
    AddResourse,
  },
  data() {
    return {
      seletedTab: 'stored-resourse',
      storedResourses: [
        {
          id: 'OfficalVue',
          title: 'OfficalVue',
          description: 'Learn more about Vue...',
          link: 'https://vuejs.org/guide/introduction.html',
        },
        {
          id: 'Google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.com',
        },
      ],
    };
  },
  computed: {
    storedResoursesMode() {
      return this.seletedTab === 'stored-resourse' ? null : 'flat';
    },
    addResoursesMode() {
      return this.seletedTab === 'add-resourse' ? null : 'flat';
    },
  },
  provide() {
    return {
      resourses: this.storedResourses,
      addResource: this.addResource,
      deleteResource: this.deleteResource
    };
  },
  methods: {
    setSeletedTab(tab) {
      this.seletedTab = tab;
    },

    addResource(title, desc, url) {
      const newResource = {
        id: new Date().toISOString,
        title: title,
        description: desc,
        link: url,
      };
      this.storedResourses.unshift(newResource);
      this.seletedTab = 'stored-resourse';
    },
    deleteResource(id){
      this.storedResourses.splice(id,1)
    }
  },
};
</script>
