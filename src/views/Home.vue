<template>
  <div class="container">
    <Menu @section="selectedSection($event)"/>
    <Section1/>
    <Section2/>
  </div>
</template>

<script>
import Menu from '../components/common/Menu.vue';
import Section1 from '../components/section/Section1.vue';
import Section2 from '../components/section/Section2.vue';

export default {
  name: 'Home',
  components: {
    Section1,
    Section2,
    Menu,
  },
  mounted() {
    if (this.$route.hash !== '') {
      this.scrollToSelectedSection(this.$route.hash);
    }
  },
  methods: {
    scrollToSelectedSection(hash) {
      const sectionPosition = this.$el.querySelector(hash).offsetTop;
      window.scrollTo({
        behavior: 'smooth',
        top: sectionPosition,
      });
    },
    selectedSection(hash) {
      if (this.$route.hash !== hash) {
        this.$router.push(hash);
      }
      this.scrollToSelectedSection(hash);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
