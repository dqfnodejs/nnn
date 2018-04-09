<template>
    <div>
       <el-button
          size="mini"
          type="mini"
          @click="btn">添加</el-button>
          <div v-show='isShow'>
          <input type="text" placeholder="姓名" v-model='data.name'><input type="text" placeholder="性别" v-model='data.gender'>
        <input type="text" placeholder="state" v-model='data.state'></div>
        <el-table
    :data="arr"
    border
    style="width: 100%">
    <el-table-column
      fixed
      prop="id"
      label="学号"
      width="150">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="120">
    </el-table-column>
    <el-table-column
      prop="gender"
      label="性别"
      width="120">
    </el-table-column>
    <el-table-column label="操作">
      <template slot-scope="scope">
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                arr:[],
                data:{},
                isShow:false
            }
                
            },
        watch:{
            '$route':function(){
                this.qi()
            }
        },
        created(){
            this.qi()
        },
        methods:{
            qi:function(){
                this.$http.post('http://localhost:3000/',{state:this.$route.params.id},{emulateJSON:true}).then(e=>this.arr=e.body)
            },
            handleDelete(e) {
                console.log(e);
                this.$http.post('http://localhost:3000/del',{id:e.id},{emulateJSON:true}).then(e=>e.id=e.body)
                var k = this.arr.indexOf(e)
                this.arr.splice(k,1)
                
            },
            btn(){
                this.$http.post('http://localhost:3000/add',this.data,{emulateJSON:true})
                .then(()=>{})
                this.isShow=!this.isShow
            }
        }
    }
        
</script>
<style>
    
</style>