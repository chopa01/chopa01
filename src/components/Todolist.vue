<template>
 <div>
	 <main class="todo">
        <div class="container">
            <h1>To - Do List</h1> 
			<Todoinput @addTodo="addTodo"/>
       
 
            <ul class="todo_list">
                <li class="todo_list_tit"><p>할 일</p></li> 
				<li class="del_btn" v-for="(item, index) in todolist" :key="index">
                    <p :class="{doneStyle:item.done}"> <input type="checkbox" name="check1" v-model="item.done">{{item.todo}}  </p>
					 <ul class="todo_list_btn">
                       <!-- <li><button>수 정</button></li>-->
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
		 {done:false, todo:"공부하기"}, //날짜 추가 가능
		 {done:false, todo:"친구와 점심약속 12시"},
		 {done:false, todo:"넷플릭스 영화보기"},
		 {done:false, todo:"Vue숙제하기"},
		 {done:false, todo:"남한산성 벚꽃놀이"},
	 ]
  }
  },  
	methods: {
		addTodo(val) {
	 		this.todolist.push({done:false, todo:val});
		 
		},
		subTodo(idx){
			this.todolist.splice(idx, 1);
		},
		todo() {
			
		}
		
	}
}
</script>
 <style>
	 .doneStyle {
		 text-decoration : line-through;
		 color: lightgray;
	 }
</style>