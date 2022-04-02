<template>
  <div id="app"> 
 	<Todolist/>
  </div>
</template>

<script> 
import Todolist from './components/Todolist.vue'
	
export default {
  name: 'App',
  components: {
	Todolist
  },
data:function() {
	return{
		hello:"a",
	}
},
	methods:{
		childCall(val) {
			console.log(val);
			this.hello = val;
		}
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
