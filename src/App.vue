<template>

  <div class="container">
    <input v-model="search" type="text" placeholder="Type to search" name="search">
    <button v-on:click="loadNews" type="button">Search</button>

    <p v-if="loading">Please wait.....</p>
    
    <div v-for="article in news">
      <img :src="article.urlToImage"  alt="">

        
      <h3>{{article.title}}</h3><br>
      <h4>{{article.author}}</h4><br>
      <p>{{article.description}}</p>
      
      <a class="button" :href="article.url" target="blank">Read More</a>
      
    </div>
  </div>
</template>

<script>
import axios from 'axios'
const baseUrl = "https://newsapi.org/v2";
const apiKey = "ec9f40e635554fa2a6e35c55159ff123";
const endPoint ="/everything";

const data = {
news :[],
search:'',
loading: false
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

  if(this.search.length < 1){
    return
  }
  this.loading=true;
  this.news=[];
  let url=baseUrl + endPoint + '?q=' + this.search + '&apiKey=' + apiKey;  
  axios.get(url).then(function(response) {
  console.log(response.data.atricles)
  data.loading=false;
  data.news = response.data.articles
  }).catch(function(error) {
  console.log(error.message)
  })
  }
  	
  }
}
</script>
