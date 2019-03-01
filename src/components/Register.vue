<template>
	<div>
		<simple-menu></simple-menu>
		<div class="content">
			<div class="row">
				<div class="col-6">
					<div class="layout-font">
						<p>全球领先的在线制造服务商</p>
	          <p>构建全球制造网络</p>
	          <p>将制造在线化</p>
	          <p>让人们获得制造服务</p>
	          <p>就像获取水电一样便利</p>
					</div>
					
				</div>
				<div class="col-6">
					<div class="col-item">
						<div class="form-wrapper">
							<div class="login-header">
								<h3 class="m-login__title new-title">
                	开启云端制造之旅
            		</h3>
							</div>
							<form>
								<el-input 
									placeholder="请输入用户名,长度不超过20位" 
									v-model="username" 
									clearable
									maxlength="20"
									@blur="handleUserNameBlur"
								>
									<i slot="prefix" class="iconfont el-input__icon icon-yonghu"></i>
								</el-input>
								<div class="hint" >
									<span v-show="showusernamehint">{{usernamehint}}</span>
								</div>
								<el-input 
									placeholder="请输入密码，长度不超过10位" 
									v-model="password" 
									clearable
									maxlength="10"
									class="margin20"
									type="password"
								>
									<i slot="prefix" class="iconfont el-input__icon icon-mima"></i>
								</el-input>
								<el-input 
									placeholder="请再次输入密码" 
									v-model="re_password" 
									clearable
									maxlength="10"
									type="password"
									@blur="handlePswdBlur"
								>
									<i slot="prefix" class="iconfont el-input__icon icon-zaicishurumima"></i>
								</el-input>
								<div class="hint" >
									<span v-show="showpswdhint">{{pswdhint}}</span>
								</div>
								<el-row>
									<el-col :span="8">
										<router-link to="/login">
											<el-button 
												type="primary" 
												plain
											>
												返回
											</el-button>
										</router-link>
									</el-col>
									<el-col :span="8"><div>&nbsp;</div></el-col>
									<el-col :span="8">
										<el-button 
											type="primary"
											@click="handleSubmit"
											:disabled="cannotsubmit"
										>
											注册
										</el-button>
									</el-col>
								</el-row>
							</form>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	//引入子组件
	import SimpleMenu from './SimpleMenu';
	export default {
		name:'Register',
    data() {
      return {
        username: '',
        password:'',
        re_password:'',
        showusernamehint:false,
        showpswdhint:false,
        usernamehint:'',
        pswdhint:'',
        getdata:undefined,
      }
    },
    components:{//注册子组件
    	SimpleMenu
    },
    computed:{//计算属性
    	cannotsubmit(){
    		let usernamevalid = this.username && this.username.length<10;
    		let pswdvalid = this.password && this.re_password &&( this.password === this.re_password );
    		return  !(usernamevalid && pswdvalid);			
    	}
    },
    methods:{//方法
    	exampswds(){
    		this.showpswdhint = !(this.password === this.re_password);
    	},
    	handleUserNameBlur(){
    		if(this.username.length<1){
    			this.showusernamehint = true;
    			this.usernamehint = "用户名不能为空";
    		}else{
    			this.showusernamehint = false;
    			this.usernamehint = "";
    		}
    	},
    	handlePswdBlur(){
    		if( this.password && this.re_password && ( this.password === this.re_password ) ){
    			this.pswdhint = '';
    			this.showpswdhint = false;
    		}else{
    			this.pswdhint = '密码或重复密码不能为空，且必须一致';
  				this.showpswdhint = true;
    		}
    	},
    	handleData( data ){
    		this.getdata = data;
    	},
    	handleSubmit(){
    		//ajax请求用axios工具来实现，此处以get请求为例，post相关请查阅axios基础api
    		axios.get( '/api/index.json?city="北京"' )
				.then( this.handleData );
    	}
    }
  }
</script>

<style>
	.content{
		min-height: 780px;
		background: url('https://www.yungongchang.com/Common/Images/Layout/login_bg.png');
		background-repeat: no-repeat;
		background-size: cover;
	}
	.content div.row{
		width:1140px;
		margin:0 auto;
		display: flex;
		flex-flow: row nowrap;
	}
	div.row div.col-6{
		flex-basis: 50%;
		position: relative;
		padding:0 15px;
		box-sizing: border-box;
	}
	div.col-6 .layout-font{
		margin-top:35%;
	}
	.layout-font p{
		color: #fff;
		font-size: 30px;
		font-weight: bold;
		margin-bottom: 13px;
		line-height: .9rem;
		text-align: left;
	}
	.col-item{
		position: absolute;
		right:10px;
		width:415px;
	}
	.form-wrapper{
		border-radius: 5px;
		padding: 30px !important;
		margin: 35% auto 0 auto;
		background-color: #eceef1;
	}
	.login-header{
		margin-bottom: .2rem;
	}
	.new-title{
		color: #353535;
		text-align: center;
		font-size: 28px !important;
		font-weight: 400 !important;
	}
	.el-row{
		margin-top:10px;
	}
	.hint{
		height:20px;
		color:red;
		line-height: 20px;
		font-size: 11px;
		text-align: left;
	}
	.margin20{
		margin-bottom: 20px;
	}
</style>