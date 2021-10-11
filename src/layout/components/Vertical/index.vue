<template>
  this is layout of Vertical.
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Vertical',
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