<template>
  <div id="app">
    <el-menu
      :default-active="activeIndex2"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-menu-item index="1"><router-link to="/1">首页</router-link></el-menu-item>
      <el-menu-item index="2"><router-link to="/1">1705A</router-link></el-menu-item>
      <el-menu-item index="3"><router-link to="/2">待重修</router-link></el-menu-item>
      <el-menu-item index="4"><router-link to="/3">已重修</router-link></el-menu-item> 
    </el-menu>
    <router-view/>
  </div>
  
</template>

<script>
export default{
    created(){
        if(this.$route.params.id == null){
            this.dong="1"
        }else{
        this.dong=parseInt(this.$route.params.id)+1+""
      }
    },
    data(){
        return{
            activeIndex2:'1',
            dong:''
        }
    },
     methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  display: block;
  padding: 0 20px;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
