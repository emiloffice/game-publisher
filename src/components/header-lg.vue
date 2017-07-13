<template>
  <div class="header-lg text-center">
    <img src="../assets/img/multiverse_logo.png" alt="multiverse logo" class="logo">
    <span class="big-title">Premier Game Publisher</span>
  </div>
</template>

<script>
  export default {
    name: 'header-lg'
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" type="text/css">
  @import '../assets/scss/reset.scss';
  .header-lg{
    background: url('../assets/img/header-bg.jpg') no-repeat center;
    background-size: cover;
    height: 30rem;
    color: #ffffff;
    width: 100%;
    padding-top: 2rem;
  }
 .header-lg img.logo{
   display: block;
   text-align: center;
   max-width: 18rem;
   width: 80%;
   margin: 3rem auto;
 }
</style>
