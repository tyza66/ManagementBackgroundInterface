<template>
  <el-config-provider :locale="locale">
    <div>
      <Header />
      <div style="display:flex;">
        <Aside />
        <router-view style="flex:1;"/>
      </div>
    </div>
  </el-config-provider>
</template>

<style>
</style>

<script>
import Header from "@/components/Header"
import Aside from "./components/Aside.vue"
import { ElConfigProvider } from 'element-plus'
import zhCn from 'element-plus/lib/locale/lang/zh-cn'
export default {
  name: "Layout",
  components: {
    Header,
    Aside,
    [ElConfigProvider.name]: ElConfigProvider
  },
  data(){
    return {
      locale: zhCn
    }
  }
}
</script>