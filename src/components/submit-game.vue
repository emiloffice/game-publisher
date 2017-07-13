<template>
  <div class="submit-game container">
      <p class="title">SUBMIT YOUR GAME</p>
      <el-form :model="gameForm" :rules="rules" ref="gameForm" class="form-area">
        <el-form-item label="Your Name" prop="name">
          <el-input v-model="gameForm.name"></el-input>
        </el-form-item>
        <el-form-item label="Your Email" prop="email">
          <el-input v-model="gameForm.email"></el-input>
        </el-form-item>
        <el-form-item label="Your Company" prop="company">
          <el-input v-model="gameForm.company"></el-input>
        </el-form-item>
        <el-form-item label="Game Title" prop="gameTitle">
          <el-input v-model="gameForm.gameTitle"></el-input>
        </el-form-item>
        <el-form-item label="Game Bio" prop="gameBio">
          <el-input type="textarea" v-model="gameForm.gameBio"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('gameForm')">立即创建</el-button>
          <el-button @click="resetForm('gameForm')">重置</el-button>
        </el-form-item>
      </el-form>
  </div>
</template>

<script>
  export default {
    name: 'submit-game',
    data () {
      return {
        gameForm: {
          name: '',
          email: '',
          company: '',
          gameTitle: '',
          gameBio: ''
        },
        rules: {
          name: [
            { required: true, message: 'Please enter your name!', trigger: 'blur' }
          ],
          email: [
            { required: true, message: 'Please enter your email!', trigger: 'blur' },
            { type: 'email', message: 'Please enter the correct format of the email', trigger: 'blur,change' }
          ],
          company: [
            { required: true, message: 'Please enter your company!', trigger: 'blur' }
          ],
          gameTitle: [
            { required: true, message: 'Please enter your game title!', trigger: 'blur' }
          ],
          gameBio: [
            { required: true, message: 'Please enter your game bio!', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      submitForm (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit')
            console.log(this.gameForm)
          } else {
            console.log('error submit')
            return false
          }
        })
      },
      resetForm (formName) {
        this.$refs[formName].resetFields()
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" type="text/css">
  .submit-game{

  }
  .submit-game .title{
    font-size: 1.8rem;
    font-weight: bold;
    border-bottom: 1px solid #eeeeee;
    padding: 2rem 0;
  }
  .form-area{
    width: 90%;
    max-width: 40rem;
    margin: 3rem auto;
  }
</style>
