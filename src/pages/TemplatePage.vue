<template>
  <div class="page">
    {{msg}}
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import Menu from '../menus';

export default {
  data() {
    return {
      msg: 'Template Page',
    };
  },

  computed: Object.assign(
    {
    },
    mapGetters('ui', ['fullpage']),
  ),

  methods: Object.assign(
    {
    },
    mapActions('ui', ['toggleSidebar', 'toggleFullPage']),
  ),

  mounted() {
    this.$store.commit('ui/SET_MENU', Menu);
  },
};
</script>

<style lang="scss" scoped>
.page {
  margin: 20px;
}
</style>
