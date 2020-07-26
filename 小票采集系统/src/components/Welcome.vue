<template>
  <div>
    <h3>Welcome to 小票数据采集系统</h3>
     <img src="../assets/toux.jpg"  height="20%" width="50%" alt="">
     <!-- <el-table border
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
      <el-table-column label="描述符" prop="comparator" >
        <template slot-scope="scope">
         <el-autocomplete  v-model="scope.row.comparator" 
       @select="init()" :fetch-suggestions="querySearchAsync" placeholder="请输入内容"></el-autocomplete>
        </template>
      </el-table-column>

      <el-table-column>
 
      </el-table-column>
    </el-table> -->
  </div>
</template>
<script>
export default {
  data(){
    return {
           comparators:[{'value':'等于'},
           {'value':'小于'}],
            ApiMsg:Array(),
            tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
         
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }]
    }
  },
  methods:{
     querySearchAsync(queryString, cb) {
         cb(this.comparators)
     },
    //  formatter(row,column){
    //      console.log('2')
    //    if(row.comparator ==='等于'){
       
    //      return 'equals'
    //    }
    //  },
   init(){
       console.log(this.tableData)
     let _data=JSON.stringify(this.tableData)
           this.ApiMsg = JSON.parse(_data)
         console.log(this.ApiMsg)
         for(var i=0;i<this.ApiMsg.length;i++){
           if(this.ApiMsg[i]['comparator']=='等于')
             {this.ApiMsg[i].comparator='equals'}
           else if(this.ApiMsg[i].comparator == '小于'){
             this.ApiMsg[i].comparator = 'less_than'
           }         }
       
   }
  },
  mounted(){
    //两个数组跟着改变-浅拷贝
          //  this.ApiMsg = this.tableData;
          //  let _data=JSON.stringify(this.tableData)
          //  this.ApiMsg = JSON.parse(_data)
          //  this.init();
  }
}
</script>
