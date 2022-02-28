<template>
  <div>
    <p v-if="$fetchState.pending">fetching planets...</p>
    <p v-else-if="$fetchState.error">
      there was an error loading the page, please try later.
    </p>
    <div v-else>
      <ul>
        <li v-for="planet in planets" :key="planet.slug">
          <NuxtLink :to="planet.slug">{{ planet.title }}</NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: [],
    };
  },
  async fetch() {
    this.planets = await fetch("https://api.nuxtjs.dev/planets").then((res) =>
      res.json()
    );
  },
};
</script>
