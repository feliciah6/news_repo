<template>
  <div class="container">
    <div v-for="article in news">
      <img :src="article.urlToImage"  alt="">
        
      <h3>{{article.title}}</h3><br>
      <h4>{{article.author}}</h4><br>
      <p>{{article.description}}</p>
      
      <a class="button" :href="article.url">Read More</a>
      
    </div>
  </div>
</template>

<script>
import axios from 'axios'
const url = "https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=ec9f40e635554fa2a6e35c55159ff123";
const data = {
news :[]
}
export default {
  data: function() {
    return data
      
  },
  created() {
    this.loadNews();
  },
  methods:{

  loadNews(){
  axios.get(url).then(function(response) {
  console.log(response.data.atricles)
  data.news = response.data.articles
  }).catch(function(error) {
  console.log(error.message)
  })
  }
  	
  }
}
</script>
