<template>
  this is layout of comprehensive.
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Comprehensive',
  props: {
    device: {
      type: String,
      default() {
        return "desktop";
      },
    },
  }
})
</script>

<style>

</style>