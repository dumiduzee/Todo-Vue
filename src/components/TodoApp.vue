<template>
      <div class="container">
        <h1 class="text-center text-primary">TodoApp</h1>
        <div class="row justify-content-center">
            <div class="col-md-6">
                <!-- Input Form -->
                <div class="card shadow-sm">
                    <div class="card-body">
                        <div class="input-group mb-3">
                            <input type="text" class="form-control task-input" id="taskInput" placeholder="Enter a new task" v-model.trim="todoData">
                            <button class="btn btn-custom" @click="addTask">Add Task</button>
                        </div>
                    </div>
                </div>
                <!-- Task List -->
                <ul class="list-group" id="taskList">

                    <li v-for="(todo,index) in todoList" :key="index" class="list-group-item d-flex justify-content-between align-items-center">
                            <!-- To-Do Text -->
                            <span :class="{ 'text-decoration-line-through text-success' : todo.isDone }">{{ todo.name }}</span>

                            <!-- Buttons (Mark as Done, Delete) -->
                            <div>
                                <!-- Mark as Done Button -->
                                <button class="btn btn-sm btn-success me-2" @click="MarkDone(index)" title="Mark as Done">
                                    <span class="material-icons">Done</span>
                                </button>

                                <!-- Delete Button -->
                                <button class="btn btn-sm btn-danger" title="Delete" @click="deleteTodo(index)">
                                    <span class="material-icons">delete</span>
                                </button>
                            </div>
                        </li>
                            
                </ul>
            </div>
        </div>
    </div>
</template>


<script>


    export default{
        name:'TodoApp',
        components:{
            

        },
        data(){
            return{
                todoData:'',
                todoList:[],
                isDid:false
            }
        },
        methods:{
            addTask(){
                if (this.todoData!=='') {
                    this.todoList.push({name:this.todoData,isDone:false})
                    this.todoData = ''
                }
                
            },
            MarkDone(index){
                this.todoList[index].isDone = true
                console.log(this.todoList);
                
            },
            deleteTodo(index){
                this.todoList.splice(index,1)
            }

        }
    }
</script>

<style>

body {
            /* padding-top: 50px; */
        }

        .card {
            margin: 20px 0;
        }

        .task-input {
            width: 100%;
            padding: 10px;
        }

        .btn-custom {
            background-color: #3f51b5;
            color: white;
        }

        .btn-custom:hover {
            background-color: #2c387e;
        }

        .list-group-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
</style>