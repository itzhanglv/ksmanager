<template>
    <el-table
            :data="tableData"
            style="width: 100%">
        <el-table-column
                prop="date"
                label="评论内容"
                width="180">
        </el-table-column>
        <el-table-column
                prop="name"
                label="用户昵称"
                width="180">
        </el-table-column>
    </el-table>
</template>
<script>
    export default {
      data(){
        return {}
      },
      props:{
        tableData:{
          type:Array,
          default:function (){
            return []
          }
        }
      }
    }
</script>
<style lang="less" scoped>
    .el-table {
        /deep/.el-table__header{
            width: 100% !important;
        }

        /deep/th,tr {
            background-color: rgba(0,0,0,0.01);
            color: #000;
            font-size: 12px;
        }
        /deep/.el-table__empty-block {
            width: 100% !important;
            text-align: center;
            font-size: 12px;
        }
    }
</style>