<template>
  <div class="app-container">
    <div class="header">
        <div class="logo-name">
            <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3354365911,3284864909&fm=26&gp=0.jpg" alt="">
            <span>管理平台</span>
        </div>
        <div class="info">
            <el-badge :value="12" class="item">
            <i class="el-icon-message-solid"></i>
            </el-badge>
            <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1527900036,1449882560&fm=26&gp=0.jpg" alt="">
            <div class="personInfo">
                <label for="name">快手名:<span id="name">lishichao</span></label>
                <label for="id">快手ID:<span id="id">234342</span></label>
            </div>
            <div class="icon-right"><i class="el-icon-arrow-down"></i></div>
            
        </div>
    </div>
    <div class="body">
      <div class="navbar">
       <div class="createGG">
           <el-button type="danger" icon="el-icon-plus">创建广告</el-button>
       </div>
          <nav-menu></nav-menu>
      </div>
      <div class="content">
          <comment></comment>
      </div>
    </div>
  </div>
</template>

<script>
import  navmenu from './components/navmenu'
import comment from './components/comment/comment'
export default {
  name: 'App',
  components: {
    'nav-menu':navmenu,
    comment
  }
}
</script>

<style lang="less" scoped>
  .app-container {
      width: 100%;
      height: 100%;
    display: flex;
    flex-direction: column;
      position: relative;
    .header {
      width: 100%;
        height: 3%;
        display: flex;
        justify-content: space-between;
        padding: 15px;
        align-items: center;
        box-shadow: 1px 1px 5px rgba(0,0,0,0.2);
        .logo-name {
            img {
                width: 15%;
                border-right: 1px solid blue;
                vertical-align: middle;
            }
            span {
                margin-left: 10px;
            }
        }
        .info {
            display: flex;
            vertical-align: center;
            margin-right: 50px;
            img {
                width: 30px;
                height: 30px;
                border-radius: 50%;
                margin-left: 30px;
                vertical-align: middle;
            }
            .personInfo {
                display: flex;
                flex-direction: column;
                font-size: 12px;
                margin-left: 15px;
                span {
                    margin-left: 5px;
                }
            }
            .icon-right {
                position: relative;
                margin-left: 20px;
                i {
                    position: absolute;
                    top:50%;
                    left: 0;
                    transform:translate(-50%,-50%);
                }
            }
            
        }
    }
    .body {
      width: 100%;
        height: 97%;
        display: flex;
        justify-content: flex-start;
        .navbar {
            width: 12%;
            height: 100vh;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
            text-align: center;
            background-color: rgba(0,0,0,0.03);
            .createGG {
                margin: 25px 0;
            }
        }
        .content {
            width: 88%;
            height: 100%;
            background-color: rgba(0,0,0,0.1);
            padding:20px;
        }
    }
  }
</style>
