<template>

    <h2>Today's Tasks</h2>

    <div class="box">
      <div class="tasks">
        <div v-for="x in todos" :key="x.id" class="list-item">
          {{ x.text }}
          <button @click="remove(x.id)" class="remove-button">x</button> <!-- id as parameter -->
        </div>
      </div>
        <div class="input-buttons">
          <input @keyup.enter="addTodo" type="text" v-model="todo" class="input" placeholder="add a task">
          <button @click="addTodo" class="add-button">+</button>
          <div class="clear">
            <button @click="clear" class="clear-button">clear all</button>
          </div>
        </div>

    </div>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      todo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.todo.length === 0) {
        return
      } else {
        this.todos.push( {
          id: Math.random(),
          text: this.todo
        })
      }
      this.todo = ''
    },
    // creates a new array that only has items that don't match the parameter id
    remove(todoId) {
      this.todos = this.todos.filter(x => x.id !== todoId)
    },
    clear() {
      this.todos = []
    }
  }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:ital,wght@0,100;0,300;1,300&display=swap');

#app {
  text-align: center;
  margin-top: 80px;
}

body {
    background: linear-gradient(-80deg, hsl(59, 100%, 63%), #ffc423, #ff7300, #ff6a5f);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;
    color: white;
    font-family: 'IBM Plex Mono', monospace;
}

@keyframes gradient {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}

h2 {
  font-weight: 300;
  font-style: italic;
  font-size: 2.7rem;
}

.box {
  margin: 0 auto;
  height: 600px;
  width: 600px;
  background: rgba(169, 87, 216, 0.76);
  display: flex;
  flex-direction: column;
  background: linear-gradient(-80deg, hsl(59, 100%, 63%), #ffc423, #ff7300, #ff6a5f);
  background-size: 400% 400%;
  animation: gradient 14s ease infinite;
  border-radius: 50%;
}

.tasks {
  padding: 10%;
}

.list-item {
  margin-top: 2%;
}

.input-buttons {
  margin-top: auto;
  padding: 5%;
}

.input {
  color: white;
  background: none;
  border: none;
  border-bottom: 1px solid white;
}

::placeholder {
  color: rgba(255, 255, 255, 0.719);
  font-family: 'IBM Plex Mono', monospace;
  font-style: italic;
}

.remove-button,
.add-button,
.clear-button {
  background: none;
  border: none;
  cursor: pointer;
  font-family: 'IBM Plex Mono', monospace;
}

.remove-button {
  color: rgb(131, 29, 16);
  font-size: 1.2rem;
}

.add-button {
  color: rgb(0, 104, 26);
  font-size: 1.3rem;
}

.clear {
  margin-top: 3%;
}

.clear-button {
  color: rgba(255, 255, 255, 0.719);
  font-style: italic;
  text-transform: uppercase;
  font-size: 1.1rem;
}

</style>
