<template>
	<el-row class="part-row">
				<el-col :span="1">
					{{part.id}}
				</el-col>
				<el-col :span="3">
					<img :src="part.imgsrc">
				</el-col>
				<el-col :span="4">
					<div>零件名称：{{part.name}}</div>
					<div>长宽高：{{size}}</div>
					<div>体积：{{part.volume}}</div>
					<div>表面积：{{part.sa}}</div>
					<div>画图单位：{{part.unit}}</div>
				</el-col>
				<el-col :span="3">
					<el-select v-model="tech_val" placeholder="请选择">
				    <el-option
				      v-for="(item,index) in techused.techs"
				      :key="index"
				      :label="item"
				      :value="item">
				    </el-option>
				  </el-select>
				</el-col>
				<el-col :span="3">
					<el-select v-model="material_val" placeholder="请选择">
				    <el-option
				      v-for="(item,index) in techused.materials"
				      :key="index"
				      :label="item"
				      :value="item">
				    </el-option>
				  </el-select>
				</el-col>
				<el-col :span="2">
					<el-select v-model="sa_val" placeholder="请选择">
				    <el-option
				      v-for="(item,index) in techused.sas"
				      :key="index"
				      :label="item"
				      :value="item">
				    </el-option>
				  </el-select>
				</el-col>
				<el-col :span="4">
					<el-input-number 
						v-model="num1" 
						:min="part.defalutnum" 
						:max="10" 
						label="描述文字">
						
					</el-input-number>
				</el-col>
				<el-col :span="2">
					价格/交易日期
				</el-col>
				<el-col :span="2">
					操作
				</el-col>
			</el-row>
</template>

<script>
	//引入子组件
	import MainMenu from './MainMenu';
	export default {
		name:'SinglePart',
		props:['part','techused'],
		data(){
      return {
      	tech_val:'',
      	material_val:'',
      	sa_val:'',
      }
    },
    computed:{
    	size(){
    		return this.part.size[0]+"*"+this.part.size[1]+"*"+this.part.size[2];
    	},
    }
	}
</script>

<style>
.part-row{
	height: 158px;
	display: flex;
	flex-flow: row nowrap;
	align-items: center;
}
.part-row .el-col{
	height:100%;
	border: 1px solid #dee2e6;
	border-right: none;
}
.part-row .el-col:last-child{
	border-right:1px solid #dee2e6;
}

</style>