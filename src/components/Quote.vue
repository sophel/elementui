<template>
	<div>
		<main-menu></main-menu>
		<div class="parts-wrapper">
			<el-row class="title">
				<el-col :span="1">
					序号
				</el-col>
				<el-col :span="3">
					缩略图
				</el-col>
				<el-col :span="4">
					零件信息
				</el-col>
				<el-col :span="3">
					成型工艺
				</el-col>
				<el-col :span="3">
					材质/热处理
				</el-col>
				<el-col :span="2">
					表面处理
				</el-col>
				<el-col :span="4">
					数量
				</el-col>
				<el-col :span="2">
					价格/交易日期
				</el-col>
				<el-col :span="2">
					操作
				</el-col>
			</el-row>
			<single-part 
				v-for="(part,index) in parts.parts" 
				:part="part"
				:techused="parts.techused"
				:key="index"
			>
			</single-part>

		</div>
	</div>
</template>

<script>
	//引入子组件
	import MainMenu from './MainMenu';
	import SinglePart from './SinglePart';
	import axios from 'axios';
	export default {
		name:'Quote',
		data(){
      return {
      	parts:{},
      }
     },
    components:{
    	MainMenu,
    	SinglePart,
    },
    methods:{
    	handleData( data ){
    		let user_data = data.data;
    		if( user_data.ret ){
    			this.parts = user_data.data;
    		}
    	}
    },
    mounted(){
    	axios.get( '/api/parts.json' )
				.then( this.handleData );
    },
	}
</script>

<style scoped="scoped">
	.parts-wrapper{
		width:1200px;
		margin:20px auto;
	}
	.title{
		height:45px;
		line-height: 43px;
		background: #eee;
	}
	.title .el-col{
		border:1px solid #dee2e6;
		border-right: none;
	}
	.title .el-col:last-child{
		border-right:1px solid #dee2e6;
	}
</style>