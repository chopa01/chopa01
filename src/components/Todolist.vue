<template>
 <div>
	 <main class="todo">
        <div class="container">
            <h1>To - Do List</h1>

            <!-- ul.list_add -->
            <ul class="list_add">
                <li class="list_add_tit"><p>등록 하기</p></li>
                <li><p><input type="text"><button>등 록</button></p></li>
            </ul>
            <!--// ul.list_add -->

            <!-- ul.todo_list -->
            <ul class="todo_list">
                <li class="todo_list_tit"><p>할 일</p></li> 
				<li class="del_btn" v-for="(item, index) in todolist" :key="index" >
                    <p> <input type="checkbox" name="check1" value="">{{item.todo}}  </p>
				</li> 
            </ul>
            <!--// ul.todo_list -->

        </div>
    </main>
</div>
</template>

<script> 
 
export default {
  name: 'todolist', 
  data: function() {
  return { 
	 todolist:  [
		 {todo:"공부하기"},
		 {todo:"친구와 점심약속 12시"},
		 {todo:"넷플릭스 영화보기"},
		 {todo:"Vue숙제하기"},
		 {todo:"남한산성 벚꽃놀이"},
	 ]
  }
  },  
}
</script>
 