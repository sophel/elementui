<template>
	<div class="header">
		<div class="container">
			<router-link
			tag="a" 
			to="/"
			class="left"
			>
				<img src="https://www.yungongchang.com/Common/Images/newHome/logo.png"/>
			</router-link>

			<router-link
			tag="a" 
			to="/quote"
			class="right"
			>
				返回首页
			</router-link>
		</div>
	</div>
</template>

<script>
	export default{
		name:'SimpleMenu'
	}
</script>

<style>
	.header{
		height: 72px;
		background:#3e4d5c ;
	}
	.header .container{
		width:1110px;
		margin:0 auto;
	}
	.container a.left{
		text-decoration: none;
		float: left;
		width: 173px;
		height: 72px;
		display: flex;
		align-items: center;
	}
	.container a.right{
		float: right;
		line-height: 72px;
		font-size: 18px;
		font-weight: 500;
		color:#fff;
	}
</style>