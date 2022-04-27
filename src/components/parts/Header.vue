<template>
  <ul>
    <li>
      <router-link aria-label="Menu page" to="/">Menu</router-link>
    </li>
    <li>
      <router-link aria-label="Cart page" to="/cart">Cart ({{ cartCount }})</router-link>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapGetters } from 'vuex';

export default defineComponent({
  name: 'Header',
  computed: {
    ...mapGetters({
      cartCount: "cart/cartCount"
    })
  }
})
</script>

<style scoped>
ul {
  display: flex;
  justify-content: center;
  border-bottom: 2px solid #ddd;
  padding: 0;
  position: sticky;
  top: 0;
  z-index: 1;
  background: rgb(250, 255, 255);
  margin-block: 0;
}

li {
  list-style: none;
  padding: 10px 5px 10px 5px;
}

a {
  color: black;
  font-weight: 600;
  text-decoration: none;
}

a:hover {
  color: grey;
  text-decoration: none;
}

a.router-link-active {
  color: darkorange;
}

@media (min-width: 500px) {
  li {
    padding: 10px 8px 10px 8px;
  }

  a {
    font-size: 1.2rem;
  }
}
</style>
