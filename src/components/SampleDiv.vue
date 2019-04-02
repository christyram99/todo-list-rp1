<template>
  <div v-if="tasks.length > 0" class="todo-list-main">
    <ul id="tasks-list">
      <li class="task" v-for="task in tasks" :key="task.id" @click="editTask(task.id)" contenteditable="true"  draggable="true" ondragstart="dragstart_handler(event)" >
        {{task.text}}
      </li>
    </ul>
    <button @click="addTask()" draggable="true" ondrag="drag_handler(event);">Add</button>

    <span id="dropDiv" ondrop="drop(event)" ondragover="allowDrop(event)"> Delete </span>
  </div>

  <div v-else class="todo-list-main">
    0 Tasks.
    <br>
    <button @click="addTask()">Add</button>
  </div>
</template>

<script>
export default {
  name: 'SampleDiv',
  data () {
    return {
      msg: 'Sample Div',
      tasks: [],
      taskId: 0
    }
  },
  methods: {
    drag_handler (event) {
      console.log(' in drag handler')
    },
    dragstart_handler () {
      console.log('in dragstart_handler')
    },
    addTask () {
      this.tasks.push({
        id: this.taskId,
        text: 'new task'
      })

      this.taskId++
    },
    editTask (id) {
    },
    drop (ev) {
      console.log('in drop')
      ev.preventDefault()
      // let data = ev.dataTransfer.getData('text')
      // console.log('data ', data)
    },
    allowDrop (ev) {
      ev.preventDefault()
    },
    drag (ev) {
      console.log('in drag')
      // ev.dataTransfer.setData('Text', ev.target.id)
    },
    ram (ev) {
      console.log('in ram')
    }
  }
}
</script>

<style>
.todo-list-main {
  text-align: center;
  align-content: center;
  width: 50%;
  margin-left: 25%;
  background-color: #eeeeee;
  /* box-shadow: 0 2px 4px #eaeaea; */
}

ul > li {
  list-style: none;
  padding: 15px;
  margin-top: 5px;
  margin-bottom: 10px;
  background-color: #dedede;
  width: 90%;
  margin-left: 2%;
}

.task:hover {
  cursor: pointer;
}

.task:focus {
  cursor: text;
}
</style>
