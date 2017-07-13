<template>
  <div class="index">
    <header-lg></header-lg>
    <nav-bar></nav-bar>
    <about-ours></about-ours>
    <published></published>
    <compoent :is="tabName"></compoent>
    <footer-bar></footer-bar>
  </div>
</template>

<script>

  import headerLg from '../components/header-lg'
  import navBar from '../components/navbar'
  import aboutOurs from '../components/about-ours'
  import published from '../components/published'
  import submitGame from '../components/submit-game'
  import uploadMedia from '../components/upload-media'
  import footerBar from '../components/footer-bar'
  export default {
    name: 'index',
    components: {
      navBar, headerLg, aboutOurs, published, submitGame, footerBar, uploadMedia
    },
    data () {
      return {
//        tabName: 'submit-game'
        tabName: 'upload-media'
      }
    },
    route: {
      data: function (transition) {
        this.gerUserDetails(transition)
      }
    },
    methods: {
      getUserDetails (transition) {
        this.$http.get('/index/' + this.$route.params.userName)
          .then(function (response) {
            this.user = response.data
            transition.next()
          })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/scss/reset.scss';
</style>
