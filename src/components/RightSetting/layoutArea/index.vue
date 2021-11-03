<template>
  <el-form ref="layoutFormRef" label-position="left" class="layout-form" label-width="100px">
    <el-form-item :label="langConfig.form.layout[lang]" prop="primary">
      <el-select v-model="selectLayout" placeholder="请选择活动区域">
        <el-option v-for="item in layoutArr" :key="item.value" :label="item.label" :value="item.value">
          <span style="float: left">{{ item.label }}</span>
          <span style="float: right; color: #8492a6; font-size: 13px">{{ item.value }}</span>
        </el-option>
      </el-select>
    </el-form-item>
  </el-form>
</template>
<script>
import { defineComponent, ref, reactive, toRefs, computed } from 'vue'
import { langConfig } from '@/utils/constant/config'
import { useStore } from '@/store/index'

export default defineComponent({
    props: {
        lang: {
            type: String,
            default: '/zh-CN'
        }
    },
    setup() {
        const layoutFormRef = ref(null)
        const store = useStore();
        const state = reactive({
            // 布局种类 horizontal横向 vertical纵向 gallery画廊 comprehensive综合 common常规
            layoutArr: [{
                value: 'comprehensive',
                label: '综合'
            }, {
                value: 'vertical',
                label: '纵向'
            },
                // {
                //     value: 'horizontal',
                //     label: '横向'
                // }, {
                //     value: 'gallery',
                //     label: '画廊'
                // }, {
                //     value: 'common',
                //     label: '常规'
                // }
            ],
            selectLayout: computed({
                set: (value) => {
                    store.dispatch('settingsModule/toToggleLayout', value);
                },
                get: () => store.getters['settingsModule/getLayoutStyle'],
            }),
        })

        return {
            langConfig,
            ...toRefs(state),
            layoutFormRef

        }
    }
})
</script>
<style lang="stylus" scoped>
.layout-form {
    width: 100%;
}
</style>
