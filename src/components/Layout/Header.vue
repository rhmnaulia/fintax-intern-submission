<template>
  <header>
    <h1>Fintax Internship Submission</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>|<router-link to="/about">
        About</router-link
      >
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style scoped>
header {
  background: #16213e;
  color: #f6f6f6;
  text-align: center;
  padding: 10px;
}
header a {
  color: #e94560;
  padding-right: 5px;
  text-decoration: none;
}

header a:hover {
  color: #eb5f76;
}
</style>
