<script>
import AppForm from "./components/AppForm.vue";
import AppHeader from "./components/AppHeader.vue";
export default {
  name: 'AppVue',
  components: { AppForm, AppHeader },
};
</script>

<template>
  <AppHeader />
  <main id="main" class="mt-5">
    <AppForm />
  </main>

</template>

<style scoped></style>