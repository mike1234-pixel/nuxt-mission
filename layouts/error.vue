<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col">
          <div v-if="error.statusCode === 404">404</div>
          {{ error.statusCode }}. take me <NuxtLink to="/">home</NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["error"],
  layout: "error", // you can set a custom layout for the error page
};
</script>
