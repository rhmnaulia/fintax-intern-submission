<template>
  <v-app>
    <Header />

    <v-main>
      <router-view />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Header from './components/Layout/Header';
import Footer from './components/Layout/Footer';
export default {
  name: 'App',
  components: { Header, Footer },

  data: () => ({
    //
  }),
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,600;1,300;1,400;1,600&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.4;
}
</style>
