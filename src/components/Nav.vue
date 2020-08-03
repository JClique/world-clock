<template>
  <nav>
    <ul class="navbar">
      <li>
        <router-link to="/">Home</router-link>
      </li>
      <li>
        <h1>
          World-Clock
        </h1>
      </li>
      <li>
        <router-link to="/about">About</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Nav',
  props: {
  }
}
</script>

<style scoped>
nav {
  margin: 1rem auto;
}

ul.navbar {
  list-style: none;
  display: flex;
  justify-content: space-around;
  margin: auto;
  padding: 0;
  max-width: 800px;
  font-family: 'Open Sans', sans-serif;
  font-size: 1rem;
  font-weight: 500;
}

ul.navbar li {
  padding: 1rem;
}

ul.navbar li:nth-child(2) {
  padding: 1rem 0;
}

h1 {
  font-family: 'Cinzel', serif;
  font-size: 2rem;
  margin: 0;
  padding: 0;
  vertical-align: top;
  line-height: 0.8;
  white-space: nowrap;
}
</style>
