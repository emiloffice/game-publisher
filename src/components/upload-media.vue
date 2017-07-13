<template>
  <div class="upload-media">
    <p class="title">UPLOAD IMAGES</p>
    <el-upload
      class="upload-images"
      action="https://jsonplaceholder.typicode.com/posts/"
      :on-preview="handlePreview"
      :on-remove="handleRemove"
      :file-list="fileList2"
      list-type="picture">
      <el-button size="small" type="primary">click to upload images</el-button>
      <div slot="tip" class="el-upload__tip">Can only upload jpeg / png files, and a single file size can not exceed 500Kb</div>
    </el-upload>
    <p class="title">ADD THE URL OF YOUR GAME VIDEOS</p>
    <el-form ref="formData" :model="formData" class="upload-videos" :rules="rules">
      <el-form-item
        v-for="(domain, index) in formData.domains"
        :label="'URL' + (index+1)"
        :key="domain.key"
        :prop="'domains.' + index + '.value'"
        :rules="rules.url">
        <div class="input-area">
        <el-input v-model="domain.value"></el-input><!--<el-button @click.prevent="removeUrl(domain)">删除</el-button>-->
        </div>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('formData')">SUBMIT</el-button>
        <el-button @click="addUrl">ADD</el-button>
        <el-button @click="resetForm('formData')">RESET</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  import ElForm from '../../node_modules/element-ui/packages/form/src/form'
  export default {
    components: {ElForm},
    name: 'upload-media',
    data () {
      return {
        fileList2: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}],
        formData: {
          domains: [{
            value: ''
          }]
        },
        rules: {
          url: [
            { required: true, message: 'THE URL INPUT CAN NOT BE EMAPTY!', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      submitForm (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit')
          } else {
            console.log('error submit')
            return false
          }
        })
      },
      resetForm (formName) {
        this.$refs[formName].resetFields()
      },
      removeUrl (item) {
        var index = this.formData.domains.indexOf(item)
        if (index !== -1) {
          this.formData.domains.splice(index, 1)
        }
      },
      addUrl () {
        this.formData.domains.push({
          value: '',
          key: Date.now()
        })
      },
      handleRemove (file, fileList) {
        console.log(file, fileList)
      },
      handlePreview (file) {
        console.log(file)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" type="text/css">
  .upload-media{

  }
  .upload-media .title{
    font-size: 1.8rem;
    font-weight: bold;
  }
  .upload-media .upload-images, .upload-media .upload-videos{
    width:80%;
    max-width: 60rem;
    margin: 0 auto;
    min-height: 30rem;
    border: 1px solid #eeeeee;
    padding: 2rem;
  }
</style>
