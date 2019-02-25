
### vue简单搜索
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<!-- 生产环境版本，优化了尺寸和速度 -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<style type="text/css">
	ul{
		list-style: none;
		
	}
	ul li{
		width:40%;
		float: left;
	}
</style>
</head>
<body>
	<div id="app">
		<input v-model="key" type="text">
		<ul v-for="item in search">
			<li>{{item.names}}</li>
			<li>{{item.tel}}</li>
		</ul>
	</div>
</body>
<script>
	var vue = new Vue({
		el:'#app',
		data(){
			return{
				key:'',
				bodys:'',
				search:[]
			}
		},
		watch:{
			key:function(newValue,oldValue) {
				var that = this;
				
				if(newValue!=oldValue){
					var arrs=[];
					for(var i=0;i<that.bodys.length;i++){
						if(that.bodys[i].tel.indexOf(newValue)==0){
							arrs.push(that.bodys[i]);
							that.search=arrs;
							console.log(that.search);
						}
					}		
				}	
			}
		},
		mounted(){
			this.init();
			this.search=this.bodys
		},
		methods:{
			init(){
				this.bodys=[{'names':'熊**','tel':'15243623738'},
					{'names':'惠**','tel':'18569498484'},
					{'names':'老**','tel':'1396339597'},
					{'names':'电信安装','tel':'13348617628'},
					{'names':'左**','tel':'18390807665'},
					{'names':'周**','tel':'1828019409'}]
			}
		}
	})
</script>
</html>
```

### vue地址栏参数获取
```
console.log(this.$route.query)
```

### 路由传参
```
/loanreview/:id  //router.js路径

<router-link  :to="'/loanreview/'+items.Id"></router-link>
```
### 跳转参数
```
meta: {  
            aid:'',          
            requireAuth: true,  // 添加该字段，表示进入这个路由是需要登录的        
            }
	    
this.$router.push({name:'authercard',params:{aid:this.authercore.PeopleIdcardLiveState}})
console.log(this.$route.params.aid);	//authercard.vue    
```

