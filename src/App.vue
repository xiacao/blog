<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>
 <script>

 
export default {
  name: 'index',
  data () {
    return {
      newsListShow: [],
    }
  },
  components: {
   // NewsCell
  },
  created() {
    this.setNewsApi();
  },
  methods:{
    setNewsApi(){
      let xhr = new XMLHttpRequest();
      xhr.open("POST","/data/index");
      xhr.setRequestHeader('content-type', 'application/x-www-form-urlencoded');
      xhr.send(null);
       xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            var data= JSON.parse(xhr.responseText);
         	console.log(data);
        }
        };
    }
    

  },
}

 </script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
