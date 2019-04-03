<template>

  <div class="todo-list-main">

    <div class="user-logo-main">
      <img width="64" height="64" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMS4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDQ4Mi45IDQ4Mi45IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA0ODIuOSA0ODIuOTsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxnPgoJPGc+CgkJPHBhdGggZD0iTTIzOS43LDI2MC4yYzAuNSwwLDEsMCwxLjYsMGMwLjIsMCwwLjQsMCwwLjYsMGMwLjMsMCwwLjcsMCwxLDBjMjkuMy0wLjUsNTMtMTAuOCw3MC41LTMwLjUgICAgYzM4LjUtNDMuNCwzMi4xLTExNy44LDMxLjQtMTI0LjljLTIuNS01My4zLTI3LjctNzguOC00OC41LTkwLjdDMjgwLjgsNS4yLDI2Mi43LDAuNCwyNDIuNSwwaC0wLjdjLTAuMSwwLTAuMywwLTAuNCwwaC0wLjYgICAgYy0xMS4xLDAtMzIuOSwxLjgtNTMuOCwxMy43Yy0yMSwxMS45LTQ2LjYsMzcuNC00OS4xLDkxLjFjLTAuNyw3LjEtNy4xLDgxLjUsMzEuNCwxMjQuOUMxODYuNywyNDkuNCwyMTAuNCwyNTkuNywyMzkuNywyNjAuMnogICAgIE0xNjQuNiwxMDcuM2MwLTAuMywwLjEtMC42LDAuMS0wLjhjMy4zLTcxLjcsNTQuMi03OS40LDc2LTc5LjRoMC40YzAuMiwwLDAuNSwwLDAuOCwwYzI3LDAuNiw3Mi45LDExLjYsNzYsNzkuNCAgICBjMCwwLjMsMCwwLjYsMC4xLDAuOGMwLjEsMC43LDcuMSw2OC43LTI0LjcsMTA0LjVjLTEyLjYsMTQuMi0yOS40LDIxLjItNTEuNSwyMS40Yy0wLjIsMC0wLjMsMC0wLjUsMGwwLDBjLTAuMiwwLTAuMywwLTAuNSwwICAgIGMtMjItMC4yLTM4LjktNy4yLTUxLjQtMjEuNEMxNTcuNywxNzYuMiwxNjQuNSwxMDcuOSwxNjQuNiwxMDcuM3oiIGZpbGw9IiMwMDAwMDAiLz4KCQk8cGF0aCBkPSJNNDQ2LjgsMzgzLjZjMC0wLjEsMC0wLjIsMC0wLjNjMC0wLjgtMC4xLTEuNi0wLjEtMi41Yy0wLjYtMTkuOC0xLjktNjYuMS00NS4zLTgwLjljLTAuMy0wLjEtMC43LTAuMi0xLTAuMyAgICBjLTQ1LjEtMTEuNS04Mi42LTM3LjUtODMtMzcuOGMtNi4xLTQuMy0xNC41LTIuOC0xOC44LDMuM2MtNC4zLDYuMS0yLjgsMTQuNSwzLjMsMTguOGMxLjcsMS4yLDQxLjUsMjguOSw5MS4zLDQxLjcgICAgYzIzLjMsOC4zLDI1LjksMzMuMiwyNi42LDU2YzAsMC45LDAsMS43LDAuMSwyLjVjMC4xLDktMC41LDIyLjktMi4xLDMwLjljLTE2LjIsOS4yLTc5LjcsNDEtMTc2LjMsNDEgICAgYy05Ni4yLDAtMTYwLjEtMzEuOS0xNzYuNC00MS4xYy0xLjYtOC0yLjMtMjEuOS0yLjEtMzAuOWMwLTAuOCwwLjEtMS42LDAuMS0yLjVjMC43LTIyLjgsMy4zLTQ3LjcsMjYuNi01NiAgICBjNDkuOC0xMi44LDg5LjYtNDAuNiw5MS4zLTQxLjdjNi4xLTQuMyw3LjYtMTIuNywzLjMtMTguOGMtNC4zLTYuMS0xMi43LTcuNi0xOC44LTMuM2MtMC40LDAuMy0zNy43LDI2LjMtODMsMzcuOCAgICBjLTAuNCwwLjEtMC43LDAuMi0xLDAuM2MtNDMuNCwxNC45LTQ0LjcsNjEuMi00NS4zLDgwLjljMCwwLjksMCwxLjctMC4xLDIuNWMwLDAuMSwwLDAuMiwwLDAuM2MtMC4xLDUuMi0wLjIsMzEuOSw1LjEsNDUuMyAgICBjMSwyLjYsMi44LDQuOCw1LjIsNi4zYzMsMiw3NC45LDQ3LjgsMTk1LjIsNDcuOHMxOTIuMi00NS45LDE5NS4yLTQ3LjhjMi4zLTEuNSw0LjItMy43LDUuMi02LjMgICAgQzQ0Nyw0MTUuNSw0NDYuOSwzODguOCw0NDYuOCwzODMuNnoiIGZpbGw9IiMwMDAwMDAiLz4KCTwvZz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K" />
    </div>
    <div class="todo-list">
      <div v-if="tasks.length > 0" class="">
        <ul id="tasks-list">
          <li class="task" v-for="(task, index) in tasks" :key="task.id" :index="index" contenteditable="true"  draggable="true" @dragstart="drag_start" >
            {{task.text}}
          </li>
        </ul>
      </div>

      <div v-else>
        <br/>
        <span style="opacity: 0.7; font-weight: 500;"> 0 Tasks. </span>
      </div>
    </div>
    <br>
    <div class="stable-div">
      <img @drop="drop" @dragover="drag_over" width="40" height="40" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDUxMiA1MTIiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDUxMiA1MTI7IiB4bWw6c3BhY2U9InByZXNlcnZlIiB3aWR0aD0iNTEycHgiIGhlaWdodD0iNTEycHgiPgo8Zz4KCTxnPgoJCTxnPgoJCQk8cG9seWdvbiBwb2ludHM9IjM1My41NzQsMTc2LjUyNiAzMTMuNDk2LDE3NS4wNTYgMzA0LjgwNyw0MTIuMzQgMzQ0Ljg4NSw0MTMuODA0ICAgICIgZmlsbD0iIzAwMDAwMCIvPgoJCQk8cmVjdCB4PSIyMzUuOTQ4IiB5PSIxNzUuNzkxIiB3aWR0aD0iNDAuMTA0IiBoZWlnaHQ9IjIzNy4yODUiIGZpbGw9IiMwMDAwMDAiLz4KCQkJPHBvbHlnb24gcG9pbnRzPSIyMDcuMTg2LDQxMi4zMzQgMTk4LjQ5NywxNzUuMDQ5IDE1OC40MTksMTc2LjUyIDE2Ny4xMDksNDEzLjgwNCAgICAiIGZpbGw9IiMwMDAwMDAiLz4KCQkJPHBhdGggZD0iTTE3LjM3OSw3Ni44Njd2NDAuMTA0aDQxLjc4OUw5Mi4zMiw0OTMuNzA2QzkzLjIyOSw1MDQuMDU5LDEwMS44OTksNTEyLDExMi4yOTIsNTEyaDI4Ni43NCAgICAgYzEwLjM5NCwwLDE5LjA3LTcuOTQ3LDE5Ljk3Mi0xOC4zMDFsMzMuMTUzLTM3Ni43MjhoNDIuNDY0Vjc2Ljg2N0gxNy4zNzl6IE0zODAuNjY1LDQ3MS44OTZIMTMwLjY1NEw5OS40MjYsMTE2Ljk3MWgzMTIuNDc0ICAgICBMMzgwLjY2NSw0NzEuODk2eiIgZmlsbD0iIzAwMDAwMCIvPgoJCTwvZz4KCTwvZz4KPC9nPgo8Zz4KCTxnPgoJCTxwYXRoIGQ9Ik0zMjEuNTA0LDBIMTkwLjQ5NmMtMTguNDI4LDAtMzMuNDIsMTQuOTkyLTMzLjQyLDMzLjQydjYzLjQ5OWg0MC4xMDRWNDAuMTA0aDExNy42NHY1Ni44MTVoNDAuMTA0VjMzLjQyICAgIEMzNTQuOTI0LDE0Ljk5MiwzMzkuOTMyLDAsMzIxLjUwNCwweiIgZmlsbD0iIzAwMDAwMCIvPgoJPC9nPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+Cjwvc3ZnPgo=" />
      &nbsp; &nbsp;
      <!-- <img  src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDQyIDQyIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA0MiA0MjsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+Cjxwb2x5Z29uIHBvaW50cz0iNDIsMTkgMjMsMTkgMjMsMCAxOSwwIDE5LDE5IDAsMTkgMCwyMyAxOSwyMyAxOSw0MiAyMyw0MiAyMywyMyA0MiwyMyAiIGZpbGw9IiMwMDAwMDAiLz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" /> -->
      <img @click="addTask()" class="cursor" width="40" height="40" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDUwIDUwIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MCA1MDsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxjaXJjbGUgc3R5bGU9ImZpbGw6IzQzQjA1QzsiIGN4PSIyNSIgY3k9IjI1IiByPSIyNSIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIyNSIgeTE9IjEzIiB4Mj0iMjUiIHkyPSIzOCIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIzNy41IiB5MT0iMjUiIHgyPSIxMi41IiB5Mj0iMjUiLz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" />
    </div>
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
    addTask () {
      console.log('called add task')
      this.tasks.push({
        id: this.taskId,
        text: 'Task ' + ( this.taskId + 1 )
      })

      this.taskId++
    },
    drag_start (event) {
      console.log(' in drag start handler')
      event.dataTransfer.setData('index', event.target.getAttribute('index'))
    },
    drag_over (event) {
      console.log(' in drag over handler')
      event.preventDefault()
    },
    drop (event) {
      console.log('in drop')
      event.preventDefault()
      let index = event.dataTransfer.getData('index')
      console.log('index ', index)
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style>
.todo-list {
  text-align: center;
  align-content: center;
  overflow-y: auto;
  margin-top: 15px;
  background-color: white;
}

.todo-list-main {
  width: 50%;
  margin: 0 auto;

  background-color: white;
  /* padding: 10px 0px 20px 0px; */
  min-height: 95%;
  margin-top: 20px;
  position: relative;
  /* height: 90%; */
  /* position: absolute; */
  box-shadow: 0 2px 5px 0.8px #bebebe;
  border-radius: 4px;
}

ul > li {
  list-style: none;
  padding: 18px;
  margin-top: 25px;
  margin-bottom: 10px;
  width: 90%;
  background-color: #f2f2f2;
  border-radius: 6px;
  box-shadow: 0 2px 4px 0.3px #c9c9c9
}

.task:hover {
  cursor: pointer;
}

.task:focus {
  cursor: text;
}

.user-logo-main {
  /* margin-top: 20px; */
  text-align: center;
  align-content: center;
  background-color: #eeeeee;
  padding: 20px 0px 20px 0px;
}

.cursor:hover {
  cursor: pointer;
}

.stable-div {
  /* margin-bottom: 0; */
  /* position: absolute; */
  right: 0;
  text-align: center;
  align-content: center;
  padding: 0px 0px 20px 0px;
}
</style>
