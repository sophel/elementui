<template>
	<div>
		<el-menu
		  :default-active="activeIndex2"
		  class="el-menu-demo"
		  mode="horizontal"
		  background-color="#343a40"
		  text-color="#fff"
		  active-text-color="#ffd04b">
		  <el-menu-item index="7">
		  	<a href="https://www.ele.me" target="_blank">
		  		<img src="https://www.yungongchang.com/Common/Images/newHome/logo.png" />
		  	</a>
		  </el-menu-item>
		  <el-submenu index="1" 
		  	show-timeout=0
		  	hide-timeout=0
		  >
		  	<template slot="title">关于我们</template>
		  	<el-menu-item index="1-1">公司介绍</el-menu-item>
		  	<el-menu-item index="1-2">主创团队</el-menu-item>
		  	<el-menu-item index="1-3">核心技术</el-menu-item>
		  	<el-menu-item index="1-3">公司动态</el-menu-item>
		  	<el-menu-item index="1-3">强大制造产能</el-menu-item>
		  </el-submenu>
		  <el-submenu index="2" 
		  	show-timeout=0
		  	hide-timeout=0
	  	>
		    <template slot="title">主营业务</template>
		    <el-menu-item index="2-1">手板加工</el-menu-item>
		    <el-menu-item index="2-2">3D打印</el-menu-item>
		    <el-menu-item index="2-3">机加工</el-menu-item>
		  </el-submenu>
		  <el-submenu index="3" 
		  	show-timeout=0
		  	hide-timeout=0
	  	>
		    <template slot="title">资讯</template>
		    <el-menu-item index="3-1">材料介绍</el-menu-item>
		    <el-menu-item index="3-2">工艺介绍</el-menu-item>
		    <el-menu-item index="3-3">技术应用</el-menu-item>
		    <el-menu-item index="3-4">行业动态</el-menu-item>
		  </el-submenu>
		  <el-menu-item index="4">云模型</el-menu-item>
		  <el-menu-item index="5">会员中心</el-menu-item>
		  <el-menu-item index="6">
		  	<router-link
				tag="a" 
				to="/register"
				>
				注册
				</router-link>
		  </el-menu-item>
		  <el-menu-item index="7">
	  		<router-link
				tag="a" 
				to="/login"
				>
	  		登录
	  	  </router-link>
		  </el-menu-item>
		  
		</el-menu>
	</div>
</template>

<script>
	export default {
		name: 'MainMenu',
    data() {
      return {
        activeIndex2: '4'
      };
    }
  }
</script>

<style>
	.el-menu--horizontal > .el-submenu .el-submenu__title{
		height: 72px;
		line-height:72px;
		font-size:16px;
	}
	.el-menu--horizontal {
    width: 100%;
	}
	.el-menu--popup{
		display: flex;
		flex-flow: row nowrap;
		padding: 0;
		margin:0;
	}
</style>