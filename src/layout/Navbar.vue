<template>
<section class="hero app-navbar is-dark " v-if="this.$store.state.ui.navbar">
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand nav bg-primary" style="float:left">

      <div class="navbar-item">
      <h2>VueFire CMS</h2>
      </div>

      <button class="button navbar-burger is-dark" v-on:click="toggleSidebar">
        <span></span>
        <span></span>
        <span></span>
      </button>

    </div>
    <div class="navbar-menu">
      <div class="navbar-start">

        <!-- <a class="navbar-item" href="/">Website</a> -->

        <router-link class="navbar-item" to="/">
        <i class="fa fa-empire"></i>
          Dashboard
        </router-link>
      </div>

      <div class="navbar-end">
        <a class="navbar-item" @click="logout()">
          <i class="fa fa-sign-out"></i>
          Logout
        </a>
      </div>
    </div>
  </nav>
</section>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  methods: Object.assign({
    logout() {
      this.$firebase.auth().signOut();
      this.$store.commit('ui/SHOW_FULLPAGE', true);
      this.$store.commit('ui/SHOW_LEVELBAR', false);
      this.$store.commit('user/SET_USER', { displayName: '', email: '' });
      this.$router.push('/login');
    },
  },
  mapActions('ui', ['toggleSidebar']),
  ),
};
</script>

<style lang="scss" scoped>
.app-navbar {

  position: fixed;
  min-width: 100%;
  z-index: 3;
  disable-box-shadow: 0 2px 3px rgba(17, 17, 17, 0.1), 0 0 0 1px rgba(17, 17, 17, 0.1);

  .container {
    margin: auto 10px;
  }

  .navbar-item i {
    padding-right:4px;
  }
}

.button.navbar-burger {
  border: 0px;
  border-radius: 0px;
  background-color: transparent;
}

.button.navbar-burger:active,
.button.navbar-burger:hover {
  box-shadow: 0;
  border: 0px;
}

.navbar-brand {
  min-width: 200px;
}

.navbar-brand.nav h2 {
  color: #fff;
  font-weight: bold;
}
</style>
