<template>
  <div class="top-container">
    <div class="left-box">
      <div class="icon-wrapper">
        <span class="iconfont icon-home" @click="$router.replace('/')" />
        <span class="iconfont icon-sami-select" />
        <span class="iconfont icon-full-screen" />
      </div>
      <div class="history-wrapper">
        <span class="iconfont icon-arrow-lift" @click="$router.go(-1)" />
        <span class="iconfont icon-arrow-right" @click="$router.go(1)" />
      </div>
    </div>
    <div class="right-box">
      <el-input v-model.trim="query" size="small" placeholder="搜索" @keyup.enter.native="toResult">
        <i slot="prefix" class="el-input__icon el-icon-search" />
      </el-input>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from '@vue/composition-api'
export default {
  name: 'Top',
  setup(props, { root }) {
    const state = reactive({
      query: ''
    })

    const toResult = () => {
      if (!state.query) {
        root.$message.warning('请输入查询内容')
      } else {
        root.$router.push(`/result?keywords=${state.query}`)
      }
    }

    return { ...toRefs(state), toResult }
  }
}
</script>
