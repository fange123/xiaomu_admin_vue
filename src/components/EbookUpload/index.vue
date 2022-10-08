<!--  -->
<template>
  <div class="upload-container">
    <el-upload
     :action="action"
     :headers="headers"
     :multiple="false"
     :limit="1"
     :before-upload="beforeUpload"
     :on-success="onSuccess"
     :on-error="onError"
     :on-remove="onRemove"
     :file-list="fileList"
     :on-exceed="onExceed"
     :disabled="disabled"
     drag
     show-file-list
     accept="application/epub+zip"
     class="image-upload"
     >
      <i class="el-icon-upload"></i>
      <div class="el-upload__text" v-if="!fileList.length">请将电子书拖入或<em>点击上传</em></div>
      <div class="el-upload__text" v-else>电子书已上传</div>
    </el-upload>

  </div>
</template>

<script>
  import { getToken } from '@/utils/auth'
export default {
    name:'index',
    data() {
        return {
          action:`${process.env.VUE_APP_BASE_API}/api/book/upload`,
          fileList:[],
          disabled:false
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

    },
    methods: {
      beforeUpload(file){
        console.log(file);
        this.$emit('beforeUpload',file);
      },
      onSuccess(){},
      onError(err){
      const errorMsg = JSON.parse(err.message)
        this.$message({
          message:errorMsg && errorMsg.msg || '上传失败',
          type:'error'

          })
      },
      onRemove(){},
      onExceed(){
        this.$message({
          message: '每次只能上传一本电子书',
          type: 'warning'
        })
      },
    }
}
</script>
<style scoped>

</style>
