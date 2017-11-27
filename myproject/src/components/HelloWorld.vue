<template>
	<div>
		<el-tabs v-model="activeNames">
			<el-tab-pane v-for="(item,key,index) in findTest" :label="key" :name="'key'+index">
				<el-tabs v-model="activeName2" type="card">
					<el-tab-pane v-for="(classlist,key2,index2) in item" :label="key2" :name="'keys'+index2">
						<button class="course_item" v-for="(subList,index3) in classlist" v-if="index3<3">
						{{subList}}
					 </button>
						<!--下拉菜单-->
						<el-dropdown v-else-if="index3>=3">
							<el-button type="primary" @click="fn_showFlag">
								更多菜单<i class="el-icon-arrow-down el-icon--right"></i>
							</el-button>
							<el-dropdown-menu slot="dropdown">
								<el-dropdown-item v-for="(subList,index3) in classlist" v-if="show_flag && index3>=3">{{subList}}</el-dropdown-item>
							</el-dropdown-menu>
						</el-dropdown>
					</el-tab-pane>
				</el-tabs>
			</el-tab-pane>
		</el-tabs>

		<div style="margin-top: 15px;">
			<el-input placeholder="请输入内容" v-model="input5" class="input-with-select">
				<el-select v-model="select" slot="prepend" v-on:change="getType($event)" id="typeSelect" style="width: 150px;">
					<el-option label="餐厅名" value="canguang"></el-option>
					<el-option label="订单号" value="orderNo"></el-option>
					<el-option label="用户电话" value="phone"></el-option>
				</el-select>
				<el-button slot="append" icon="el-icon-search"></el-button>
			</el-input>
		</div>

	</div>
</template>

<script>
	export default {
		name: 'HelloWorld',
		data() {
			return {

				input5: '',
				select: 'phone',
				activeNames: 'key0',
				activeName2: 'keys0',
				show_flag: false,
				findTest: {
					'all': {
						"web前端": ["HTML", "vuejs", "js", "bootsrap"],
						//						"web前端":{
						//							"HTML":["测试一","测试二","测试三"],
						//							"vuejs":"",
						//							"js":"",
						//							"bootsrap":""
						//						}

						"后台": ["java"],
						"开发工具": ["git", "svn"]
					},
					"me": {
						"web前端": ["hmtl"]
					},
					"other": {
						"web前端": ["HTML", "vuejs", "js", "bootsrap"],
						"后台": ["java"],
						"开发工具": ["git", "svn"]
					}
				}
			}
		},
		methods: {
			//			hideMoreBtn:function(){
			//			 var btns=	$(".course_item");
			//			 if(btns.length>3){
			//			 	 
			//			 }
			//			}
			fn_showFlag: function() {
				this.show_flag = true;
			},
			getType(event) {
				console.log(event);
				//				var typeSelect =thisE.label;
				//				alert(typeSelect)
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.el-tabs--card>>>.el-tabs__header {
		border-bottom: none;
	}
	
	.el-tabs--card>>>.el-tabs__header .el-tabs__item.is-active {
		border-bottom: 1px solid #cacaca;
		background: lightblue;
		color: white;
	}
	
	.el-tabs--card>>>.el-tabs__header .el-tabs__item {
		border: 1px solid #cacaca;
		margin-left: 10px;
	}
	
	.el-tabs--card>>>.el-tabs__header .el-tabs__nav {
		border: none;
	}
	/*更多按钮下拉菜单样式*/
	
	.el-dropdown {
		vertical-align: top;
	}
	
	.el-dropdown+.el-dropdown {
		margin-left: 15px;
	}
	
	.el-icon-arrow-down {
		font-size: 12px;
	}
	
	.el-select .el-input {
		width: 150px;
	}
	
	.input-with-select .el-input-group__prepend {
		background-color: #fff;
	}
	
	.el-input-group__prepend>>>div.el-select .el-input__inner {
		width: 150px;
	}
</style>