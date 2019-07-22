<template>
  <div class="row">
    <div class="col-4 card text-white bg-dark mb-4" style="max-width: 32%;" v-for="post in posts" :key="post.id">
    <h3>{{post.id}} {{post.name}}</h3>
    <p>{{post.email}}<br> {{post.body}}</p>
    </div>

  </div>

  
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
// import Vue from 'vue'
// import BootstrapVue from 'bootstrap-vue'


export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data(){
    return {
      posts: []
    }
  },
  mounted() {
    var comment = this;
    axios.get('https://jsonplaceholder.typicode.com/comments')
    .then(function(res){
      comment.posts = res.data;
      console.log('Data:',res.data);
    })
    .catch(function(error){
      console.log('error:',error);
    })
  },
}
</script>
<style scoped>
.row {
  margin: 2% 0% 0% 0%;
}
.col-4{
  margin:0% 0% 0% 1%;
}
p{
  text-align:left;
  margin-left:3vw;
}
</style>
