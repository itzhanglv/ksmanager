<template>
    <el-table
            ref="multipleTable"
            :data="tableData"
            tooltip-effect="dark"
            style="width: 100%"
            @selection-change="handleSelectionChange">
        <el-table-column
                fixed
                type="selection"
                width="55">
        </el-table-column>
        <el-table-column
                label="评论内容"
                width="120">
            <template slot-scope="scope">{{ scope.row.comments }}</template>
        </el-table-column>
        <el-table-column
                prop="name"
                label="点赞数"
                width="120">
            <span slot-scope="scope">{{scope.row.click}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="发布时间"
                show-overflow-tooltip>
            <span slot-scope="scope">{{scope.row.publish_time}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="用户昵称"
                show-overflow-tooltip>
            <span slot-scope="scope">{{scope.row.username}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="评论层级"
                show-overflow-tooltip>
            <span slot-scope="scope">{{scope.row.level}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="关联创意"
                show-overflow-tooltip>
            <span slot-scope="scope">{{scope.row.creative}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="处理状态"
                show-overflow-tooltip>
            <span slot-scope="scope">{{scope.row.state?'已回复':'-- --'}}</span>
        </el-table-column>
        <el-table-column
                prop="address"
                label="操作"
                show-overflow-tooltip>
            <el-button type="text" size="mini" @click="lookUp">查看</el-button>
            <el-button type="text" size="mini" @click="reply">回复</el-button>
        </el-table-column>
    </el-table>
</template>
<script>
    export default {
      data(){
        return {
          multipleSelection: [],
        }
      },
      methods:{
        handleSelectionChange(val) {
          this.multipleSelection = val;
        },
        reply(){
          this.$emit('reply',event.target)
        },
        lookUp(){
          this.$emit('lookUp')
        }
      },
      props:['tableData']
    }
</script>
<style lang="less" scoped>
 .el-table {
     /deep/ th, tr {
         background-color: rgba(0, 0, 0, 0.01);
         color:#000;
         font-size: 12px;
         font-family:华文细黑,MicrosoftYaHe;
     }
     /deep/ tbody {
         td {
             font-size: 10px;
         }
     }
 }


</style>