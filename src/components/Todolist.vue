<template>
 <div>
	 <main class="todo">
        <div class="container">
            <h1>To - Do List</h1> 
			<Todoinput @addTodo="addTodo"/>
            <ul class="todo_list">
                <li class="todo_list_tit"><p>할 일</p></li> 
				
				<li>
			 
					<p>	 
				{{remaining}} / {{todolist.length}} 건 처리 </p>
				<button @click="cleanTodo()">
					처리완료삭제</button>		
				</li>
				<li class="del_btn" v-for="(item, index) in todolist" :key="index">
                    <p :class="{doneStyle:item.done}"> <input type="checkbox" name="check1" v-model="item.done">{{item.todo}}  </p>
					 <ul class="todo_list_btn">  
						 {{item.regDate}} 
                        <li><button  @click="subTodo(index)">삭 제</button></li>
                    </ul>
				</li> 
            </ul>
    

        </div>
    </main>
</div>
</template>

<script> 
import Todoinput from './Todoinput.vue' 
	
export default {
  name: 'todolist', 
  components: {
	Todoinput
},
  data: function() {
  return {  
	 todolist:  [
		 {done:false, todo:"공부하기", regDate:"4/09"}, //날짜 추가 가능
		 {done:false, todo:"친구와 점심약속 12시", regDate:"4/09"},
		 {done:false, todo:"넷플릭스 영화보기", regDate:"4/09"},
		 {done:false, todo:"Vue숙제하기", regDate:"4/09"},
		 {done:false, todo:"남한산성 벚꽃놀이", regDate:"4/09"},
	 ]
  }
  },  
computed:{
		remaining() {
			return this.todolist.filter(function(val){
		 
				return val.done;
			}).length; 
		 
		},
		sortedTodo() {
		 
			return this.todolist.filter(todolist => this.todolist.done);
		}
},
	methods: {
		addTodo(val) {
		 
			var cd = new Date(); // 현재날짜
			var todo_regdate = cd.getMonth()+1 + '/'+ cd.getDate();
		 
	 		//this.todolist.push({done:false, todo:val, regDate:todo_regdate});
			this.todolist.splice(0,0,{done:false, todo:val, regDate:todo_regdate});
		 
		},
		subTodo(idx){
			if(confirm("정말 삭제하시겠습니까?")) {
			this.todolist.splice(idx, 1);
			}
		},
		cleanTodo() {
			this.todolist = this.todolist.filter(function(val){
				return val.done == false;
			})
		}
		
	},
 
	}
 
</script>
 <style>
	 .doneStyle {
		 text-decoration : line-through;
		 color: lightgray;
	 }
</style>