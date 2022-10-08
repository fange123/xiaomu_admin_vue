<!--  -->
<template>
  <el-form>
    <Sticky :class-name="'sub-navbar'">
      <el-button @click="showGuide" v-if="!isEdit">显示帮助</el-button>
      <el-button
        style="margin-left:10px"
        type="success"
        v-loading="loading"
        @click="submitForm"
        >
        {{isEdit ? '编辑电子书':'新增电子书'}}
      </el-button>
    </Sticky>
    <div class="detail-container">
      <el-row>
        <el-col :span="24">
          <EbookUpload/>
          <!-- 编写具体的表单的空间 -->
        </el-col>
      </el-row>

    </div>

  </el-form>
</template>

<script>
import Sticky from '@/components/Sticky'
import EbookUpload from '@/components/EbookUpload'
export default {
    name:'Detail',
    components:{
      Sticky,
      EbookUpload
    },
    props:{
      isEdit:Boolean
    },
    data() {
        return {
          loading:false

        }
    },
    //生命周期 - 创建完成（访问当前this实例）
    created() {

    },
    //生命周期 - 挂载完成（访问DOM元素）
    mounted() {

    },
    methods: {
      submitForm(){
        this.loading = true
        setTimeout(()=> {
          this.loading = false

        },1000)
      },
      showGuide(){
        console.log('show');
      }
    }
}
</script>
<style  scoped>
  .detail-container {
    padding:30px 50px 40px
  }

</style>
