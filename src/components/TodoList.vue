<template>
     <div id = "app">
            <h1>ToDo's Manager</h1>
            <div id="ajout-todo"></div>
            <input type="text" name="newTodo" id="newTodo" v-model="newTodo" @keyup.enter="addTodo"/>
            <div class="main">
                <ul class="todoList">
                    <li class="todo" v-for= "todo in todos">
                        <label>{{ todo.name }}</label>
                    </li>
                </ul>
            </div>
        </div>

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
        }

    },
    methods: {
        addTodo () {
            this.todos.push({
                completed: false,  
                name: this.newTodo  

            })
            this.newTodo= ""
//     document.getElementById('todos-list').innerHTML = " "
//     for(let index = 0; index < todos.length; index++) {
//         let nouvelleBalise = document.createElement('p')
//         nouvelleBalise.innerHTML = todos[index] + '<input type="submit" value="V" onclick ="removeTodo(' + index + ')">'
//         document.getElementById('todos-list').appendChild(nouvelleBalise)
//     }
 }

// function addTodo() {
//     todos.push(document.getElementById('newTodo').value)
//     ecrireTodos()
// }

// function removeTodo(index) {
//     todos.splice(index, 1)
//     ecrireTodos()
// }

// ecrireTodos()

    }
}



</script>

<style></style>