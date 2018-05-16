<template>
  <div id="app">
    <nav class="navbar is-danger is-fixed-top">
      <div class="container">
          <div class="navbar-brand">
            <a class="navbar-item" href="#app">
              Canada's Top Headlines
            </a>
            <!--
            <div class="navbar-burger" data-target="navbarExampleTransparentExample">
              <span></span>
              <span></span>
              <span></span>
            </div>
            -->
          </div>
          </div>
    </nav>

    <div class="container" id="main_container">
        <select-category @newCategory="newCategory"/>

        <news :articles="articles"/>
    </div>
<!--
    <footer class="footer">
      <div class="container">
        <div class="content has-text-centered">
          <p>
            <strong>News App</strong> by <a href="https://github.com/kaelanb">Kaelan B</a>. The source code is licensed
            <a href="http://opensource.org/licenses/mit-license.php">MIT</a>.
          </p>
        </div>
      </div>
    </footer>
-->
  </div>
</template>

<script>
import SelectCategory from './components/selectCategory'
import News from './components/news'

export default {
  name: 'app',
  components:{
  	'select-category':SelectCategory,
  	'news':News
  	
  },
  data () {
    return {
      category:'',
      articles:[]
    }
  },
  
  methods:{
    newCategory:function(arg){
      this.category=arg;
      this.$http.get('https://newsapi.org/v2/top-headlines', {params: {country:"ca",category:this.category}, headers: {'X-Api-Key': '65c7e61c0ddf48ffa1bb8a131f49c50e'}})
      .then(function(response){
        return JSON.parse(response.bodyText);
      })
      .then(function(response){
        this.articles=response.articles;
      })
      .catch(function(err){
        console.log(err);
      })
    }
  }
  
}
</script>

<style>
 #main_container{
      margin: 0 auto;
      margin-top:60px;
  }
  .heading{
    text-align: center;
    font-size:1.2em;
    margin-bottom:1em;
  }
</style>
