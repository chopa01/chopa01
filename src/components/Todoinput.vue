<template>
  
	  <main class="todo">
		<div class="container">
			<ul class="list_add">
				<li class="list_add_tit"><p>등록 하기</p></li>
				<li><p><input type="text" v-model="addText"  ref="cursor" @keyup.enter="addTodo"><button @click="addTodo">등 록</button></p></li>
			</ul>
		</div>
	</main>
 
</template>

<script> 
 
export default {
  name: 'todoInput', 
 data: function() {
  return { 
	 addText:''
 	 }
  }, 
methods: {
	addTodo() { 
		if(this.addText =="") {
			
			alert('할일을 적어주세요');
			this.$refs.cursor.focus();
		 
		} else {
		this.$emit("addTodo",this.addText);
		this.addText='';
		}
	},
	
}
}
</script>
 