<template>

    <section class="todoapp">
        <header class="header">
            <h1>ToDo's App</h1>
            <input type="text" name="newTodo" id="newTodo" v-model="newTodo" @keyup.enter="addTodo"/>
        </header>

        <div class="main">
            <input type="checkbox" class="toggle-all" v-model="allDone">
            <ul class="todo-list">
                <li class="todo" v-for= "todo in filteredTodos" :class="{completed: todo.completed}">
                    <div class="view">
                        <input type="checkbox" v-model="todo.completed" class="toggle">
                        <label>{{ todo.name }}</label>
                    </div>
                </li>
            </ul>
        </div>
    </section>
    
    <footer>
        <span class="todo-count"><strong>{{ remaining }}</strong> tache à faire</span>
        <ul class="filters">
            <li><a href="#" :class="{ selected: filter=== 'all' }" @click.prevent="filter = 'all'">total taches</a></li>
            <li><a href="#" :class="{ selected: filter=== 'todo' }" @click.prevent="filter = 'todo'">total à faire</a></li>
            <li><a href="#" :class="{ selected: filter=== 'done' }" @click.prevent="filter = 'done'">total faites</a></li>
        </ul>
        </footer>
</template>

<script>
export default {
    data () {
        return {
            todos: [{
                name: "tache de test",
                completed: false
            }],
            newTodo: "",
            filter: 'all'
        }

    },
    methods: {
        addTodo () {
            this.todos.push({
                completed: false,  
                name: this.newTodo
            })
            this.newTodo= ""
        }
    },
    computed: {

        allDone: {
            get () {
                return this.remaining === 0

            },

            set (value) {
                console.log('value',value)
                this.todos.forEach( todo => {
                    todo.completed = value
                    })
                }

                

            },

        
        remaining () {
           return this.todos.filter( todo => !todo.completed).length
        },
        filteredTodos () {
            if (this.filter === 'todo') {
                return this.todos.filter( todo => !todo.completed)
            }else if (this.filter === 'done') {
                return this.todos.filter( todo => todo.completed)
            }
                return this.todos
            
            
        }

    }
}



</script>

<style src="./todo.css">
</style>