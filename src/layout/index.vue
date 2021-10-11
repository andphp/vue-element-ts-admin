<template>
     <component
      :is="layout"
    ></component>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'
import { useStore } from '@/store/index'
import vertical from './components/Vertical/index.vue'
import comprehensive from './components/Comprehensive/index.vue'

export default defineComponent({
  name: 'Layout',
  components: {
    vertical,
    comprehensive
  },
  setup(){
    const store = useStore()
    const layout = computed(() => store.getters['settingsModule/getLayoutStyle'])
    return {
      layout,
    }
  }
})
</script>

<style>

</style>