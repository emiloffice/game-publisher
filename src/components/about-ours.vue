<template>
  <div class="about-ours text-center container">
    <el-row type="flex" class="row-bg" justify="center">
      <el-col :span="6" class="contents">
        <p class="title">SUCCESSFUL</p><p>An unparalleled track record of successful releases</p>
      </el-col>
      <el-col :span="6" class="contents">
        <p class="title">PROFESSIONAL</p><p>Backed by the support of a well rounded world class team</p>
      </el-col>
      <el-col :span="6" class="contents">
        <p class="title">EXCELLENCE</p><p>High quality games deserve high quality promotion</p>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: 'about-ours'
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .about-ours{
    border-bottom: 1px solid #eeeeee;
    padding: 3rem 0;
  }
  .contents{
    padding: 3rem 0;
  }
  .contents .title{
    font-weight: bolder;
    font-size: 1.8rem;
  }

</style>
