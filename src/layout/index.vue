<template>
  <div :class="classObj" class="apa-wrapper">
    <component
      :is="layout"
      :device="device"
    ></component>
    {{layout}}
  </div>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'
import { useStore } from '@/store/index'
import vertical from './components/Vertical/index.vue'

export default defineComponent({
  name: 'Layout',
  components: {
    vertical
  },
  setup(){
    const store = useStore()
    const device = computed(() => store.getters['appModule/getDeviceState'])
    const layout = computed(() => store.getters['settingsModule/getLayoutStyle'])
    const opened = computed(() => store.getters['appModule/getSidebarState'])
    const withoutAnimation = computed(() => store.getters['appModule/getSidebarAnimation'])
    const classObj = computed(() => ({
      hideSidebar: !opened.value,
      openSidebar: opened.value,
      withoutAnimation: withoutAnimation.value,
      mobile: device.value === 'mobile'
    }))
    return {
      device,
      layout,
      classObj
    }
  }
})
</script>

<style>

</style>