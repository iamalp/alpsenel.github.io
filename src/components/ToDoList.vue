<template>
    <div>
        <input type="text" class="todo-input" placeholder="What needs to be done" v-model="newTodo" @keyup.enter="addTodo">
        <div v-for="(todo,index) in todos" :key="todo.id" class="todo-item">
            <div>
                {{todo.title}}
            </div>
            <div class="remove-item" @click="removeTodo(index)">
                &times;
            </div>
        </div>
    </div> 
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      newTodo: '',
      idForTodo: 3,
      todos: [
          {
              'id': 1,
              'title': 'Finish Vue Screencast',
              'compeleted': false,
          },
          {
              'id': 2,
              'title': 'Take over patates',
              'compeleted': false,
          }
      ]
    }
  },
  methods: {
      addTodo () {
          if (this.newTodo.trim() === '') {
            return;
          }

        this.todos.push({
          id: this.idForTodo,
          title: this.newTodo,
          compeleted: false
        });

        this.newTodo = '';
        this.idForTodo++;
      },
      removeTodo(index) {
          this.todos.splice(index, 1);
      }
  }
}
</script>

<style scoped lang="scss">
    .todo-input {
        width: 100%;
        padding: 10px 18px;
        font-size: 18px;
        margin-bottom: 16px;

        &:focus {
            outline: 0;
        }
    }

    .todo-item {
        margin-bottom: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .remove-item {
        cursor: pointer;

        &:hover {
            color: black;
        }
    }
</style>