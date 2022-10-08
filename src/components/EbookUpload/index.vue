<!--  -->
<template>
  <div class="upload-container">
    <el-upload :action="action" :headers="headers">请上传</el-upload>

  </div>
</template>

<script>
  import { getToken } from '@/utils/auth'
export default {
    name:'index',
    data() {
        return {
          action:`${process.env.VUE_APP_BASE_API}/book/upload`,
        }
    },
    computed: {
      headers() {
        return {
          Authorization:`Bearer ${getToken()}`
        }
      }
    },
    //生命周期 - 创建完成（访问当前this实例）
    created() {

    },
    //生命周期 - 挂载完成（访问DOM元素）
    mounted() {

    }
}
</script>
<style scoped>

</style>
