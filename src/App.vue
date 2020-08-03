<template>
  <div id="app" :class="theme">
    <Nav />
    <router-view/>
  </div>
</template>

<script>
import Nav from '@/components/Nav.vue'

export default {
  components: {
    Nav
  },
  data() {
    return {
      theme: 'light'
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Cinzel&family=Open+Sans&display=swap");

:root {
  --gray1: #090A0B;
  --gray2: #2D3439;
  --gray3: #525D66;
  --gray4: #778692;
  --gray5: #A4AFB6;
  --gray6: #D2D7DB;
  --gray7: #e1e6e9;
}

.dark {
  --bg: linear-gradient(0deg, var(--gray3), var(--gray2));
  --bg-alt: var(--gray4);
  --txt: var(--gray6);
}

.light {
  --bg: linear-gradient(0deg, var(--gray7), var(--gray6));
  --bg-alt: var(--gray3);
  --txt: var(--gray1);
}

#app {
  width: 100%;
  height: 100vh;

  color: var(--txt);
  background: var(--bg);
  overflow: hidden;
}

body {
  margin: 0;
  padding: 0;
  font-family: 'Open Sans', sans-serif;
}

a {
  text-decoration: none;
  color: var(--txt);
}

a:hover {
  color: var(--bg-alt);
}

</style>
