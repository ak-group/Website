<template>
    <div>
        <ul class="list-group mb-3" v-if="todos.length">
            <TodoListItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo"/>
        </ul>
        <ul v-else class="list-group mb-3">
            <li class="list-group-item d-flex justify-content-between bg-light">
                <div class="text-success">
                    <h6 class="my-0">Promo code</h6>
                    <small>EXAMPLECODE</small>
                </div>
                <span class="text-success">-$5</span>
            </li>
        </ul>
    </div>
</template>

<script>
    import BaseInputText from './BaseInputText.vue'
    import TodoListItem from './TodoListItem.vue'

    let nextTodoId = 1;

    export default {
        components: {
            BaseInputText, TodoListItem
        },
        data() {
            return {
                newTodoText: '',
                todos: [
                    {
                        id: nextTodoId++,
                        text: 'Product name'
                    },
                    {
                        id: nextTodoId++,
                        text: 'Second product'
                    },
                    {
                        id: nextTodoId++,
                        text: 'Third item'
                    }
                ]
            }
        },
        methods: {
            addTodo() {
                const trimmedText = this.newTodoText.trim();
                if (trimmedText) {
                    this.todos.push({
                        id: nextTodoId++,
                        text: trimmedText
                    });
                    this.newTodoText = ''
                }
            },
            removeTodo(idToRemove) {
                this.todos = this.todos.filter(todo => {
                    return todo.id !== idToRemove
                })
            }
        }
    }
</script>