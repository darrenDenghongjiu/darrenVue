<template>
  <div class="hello">
    <h1>{{msg}}</h1>
	<h1>{{ msg2 }}</h1>
	<div v-for="name in items" class="finish">
		{{name}}
	</div>
	<div v-for="name in itemsjson">
		{{name}}
	</div>
	<div v-for="item in itemsjson2" :class="{'finish-2':item.isFinish}">
		<span :class="[divClass]" v-on:click="tab(item)">{{item.name}}</span>
		<span>{{item.age}}</span>
	</div>
	<input />
	
  </div>
</template>

<script>
/*v-html || {{mag}} v-text 不能加入标签 v-for arr and json*/
/*直接写class :class and v-bind:class 里面的采用属性需要在下面自己在定义 
:class="[divClass]"
*/
/*v-on:click="function name"*/
/*v-model <input> <select> <textarea>"*/
export default {
  data () {
    return {
      msg: '<span></span>我们的明天会更好!',
	  msg2:'你想我了吗？',
	  items:[1,2,3,4],
	  itemsjson:{
			name:'darren',
			age:'15',
			job:'web'
	  },
	 
	  itemsjson2:[
		{name:'darren',age:25,id:1, isFinish:true,},
		{name:'kevin',age:26,id:2, isFinish:false,},
	  ],
	  /*:class="[divClass]" use of method*/
	  divClass:'finish-1'
    }
  },
  methods:{
	tab:function (item){
		/*要让item在外面不能直接传值进来*/
		//item = !item;
		item.isFinish = !item.isFinish;
		console.log(item);
	},
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: red;
}
.finish{
	background:red; 
}
.finish-1 { background:blue; }
.finish-2 { color:white; font-size:50px; }
</style>
