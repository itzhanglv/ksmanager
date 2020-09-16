<template>
    <el-menu
            default-active="2"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose">
        <el-menu-item index="1">
            <i class="el-icon-house"></i>
            <span slot="title">我的首页</span>
        </el-menu-item>
        <el-menu-item index="2">
            <i class="el-icon-copy-document"></i>
            <span slot="title">推广</span>
        </el-menu-item>
        <el-submenu index="3">
            <template slot="title">
                <i class="el-icon-location"></i>
                <span>报表</span>
            </template>
            <el-menu-item-group>
                <template slot="title">分组一</template>
                <el-menu-item index="1-1">选项1</el-menu-item>
                <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
        </el-submenu>
        <el-submenu index="4">
            <template slot="title">
                <i class="el-icon-s-custom"></i>
                <span>账户</span>
            </template>
            <el-menu-item-group>
                <template slot="title">分组一</template>
                <el-menu-item index="1-1">选项1</el-menu-item>
                <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
        </el-submenu>
        <el-submenu index="5">
            <template slot="title">
                <i class="el-icon-shopping-bag-2"></i>
                <span>工具</span>
            </template>
            <el-menu-item-group>
                <template slot="title">分组一</template>
                <el-menu-item index="1-1">选项1</el-menu-item>
                <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
        </el-submenu>
        <el-menu-item index="4">
            <i class="el-icon-question"></i>
            <span slot="title">帮助中心</span>
        </el-menu-item>
    </el-menu>
</template>
<script>
    export default {
      data(){
        return {}
      },
      methods:{
        handleOpen(){
          console.log("open")
        },
        handleClose() {
          console.log("close")
        }
      }
    }
</script>
<style lang="less" scoped>
    .el-menu {
        background-color: rgba(0,0,0,0.02);
       li {
        text-align: left;
    }
    }
</style>