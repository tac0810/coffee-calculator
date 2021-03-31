<template>
  <v-app id="inspire">
    <v-slide-x-transition>
      <Nuxt />
    </v-slide-x-transition>
  </v-app>
</template>

<script>
export default {
  data: () => ({ drawer: false }),
}
</script>
