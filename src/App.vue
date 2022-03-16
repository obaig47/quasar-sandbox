<!-- This file is the main vue component of the app -->

<template>
  <!-- THIS IS WHERE LAYOUT OF APP WILL BE LOADED -->
  <router-view />
</template>
<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
});
</script>
