<template>
  <div>
    <p>{{ $route.params.slug }}</p>
    <!-- <pre>{{ $data }}</pre> -->
    <img :src="planet.image" :alt="planet.title" />
    <h1>{{ planet.title }}</h1>
    <PlanetsList />
  </div>
</template>

<script>
export default {
  transition: "bounce",
  // head function returns unique metadata for this page, using async data that was returned for the page
  head() {
    return {
      title: this.planet.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.planet.description,
        },
      ],
    };
  },
  // asyncData makes the request before loading the page, and you don't have to bind the result to your data
  async asyncData({ params }) {
    const planet = await fetch(
      "https://api.nuxtjs.dev/planets/" + params.slug
    ).then((res) => {
      if (res.ok) {
        return res.json();
      }
      throw new Error(res.status);
    });
    return { planet };
  },
};
</script>
