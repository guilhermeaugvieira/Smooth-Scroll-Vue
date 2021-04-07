<template>
  <div class="menu flex-center">
    <nav class="flex-center">
      <span
        v-for="secao in secoes"
        :key="secao.id"
        @click="selectSection(secao.hash)"
      >
        {{secao.name}}
      </span>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      secoes: [
        {
          hash: '#section1',
          name: 'S1',
          id: 1,
        },
        {
          hash: '#section2',
          name: 'S2',
          id: 2,
        },
      ],
    };
  },
  methods: {
    selectSection(hash) {
      this.$emit('section', hash);
    },
  },
};
</script>

<style lang="scss" scoped>
.menu{
  position: fixed;
  top: 15px;
  right: 15px;

  nav{
    gap: 10px;

    span{
      cursor: pointer;
    }
  }
}
</style>
