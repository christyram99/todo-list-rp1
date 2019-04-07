<template>

  <div class="todo-list-main">

    <div class="user-logo-main">
      <div class="user-logo-details-main" style="width: 70%">
        <div class="user-logo-details1">
          Hello Floyd Mullins
        </div>
        <div class="user-logo-details2">
          You have {{tasks.length}} task(s)
        </div>
      </div>
      <div class="user-logo" >
        <!-- <img width="64" height="64" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMS4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDQ4Mi45IDQ4Mi45IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA0ODIuOSA0ODIuOTsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxnPgoJPGc+CgkJPHBhdGggZD0iTTIzOS43LDI2MC4yYzAuNSwwLDEsMCwxLjYsMGMwLjIsMCwwLjQsMCwwLjYsMGMwLjMsMCwwLjcsMCwxLDBjMjkuMy0wLjUsNTMtMTAuOCw3MC41LTMwLjUgICAgYzM4LjUtNDMuNCwzMi4xLTExNy44LDMxLjQtMTI0LjljLTIuNS01My4zLTI3LjctNzguOC00OC41LTkwLjdDMjgwLjgsNS4yLDI2Mi43LDAuNCwyNDIuNSwwaC0wLjdjLTAuMSwwLTAuMywwLTAuNCwwaC0wLjYgICAgYy0xMS4xLDAtMzIuOSwxLjgtNTMuOCwxMy43Yy0yMSwxMS45LTQ2LjYsMzcuNC00OS4xLDkxLjFjLTAuNyw3LjEtNy4xLDgxLjUsMzEuNCwxMjQuOUMxODYuNywyNDkuNCwyMTAuNCwyNTkuNywyMzkuNywyNjAuMnogICAgIE0xNjQuNiwxMDcuM2MwLTAuMywwLjEtMC42LDAuMS0wLjhjMy4zLTcxLjcsNTQuMi03OS40LDc2LTc5LjRoMC40YzAuMiwwLDAuNSwwLDAuOCwwYzI3LDAuNiw3Mi45LDExLjYsNzYsNzkuNCAgICBjMCwwLjMsMCwwLjYsMC4xLDAuOGMwLjEsMC43LDcuMSw2OC43LTI0LjcsMTA0LjVjLTEyLjYsMTQuMi0yOS40LDIxLjItNTEuNSwyMS40Yy0wLjIsMC0wLjMsMC0wLjUsMGwwLDBjLTAuMiwwLTAuMywwLTAuNSwwICAgIGMtMjItMC4yLTM4LjktNy4yLTUxLjQtMjEuNEMxNTcuNywxNzYuMiwxNjQuNSwxMDcuOSwxNjQuNiwxMDcuM3oiIGZpbGw9IiMwMDAwMDAiLz4KCQk8cGF0aCBkPSJNNDQ2LjgsMzgzLjZjMC0wLjEsMC0wLjIsMC0wLjNjMC0wLjgtMC4xLTEuNi0wLjEtMi41Yy0wLjYtMTkuOC0xLjktNjYuMS00NS4zLTgwLjljLTAuMy0wLjEtMC43LTAuMi0xLTAuMyAgICBjLTQ1LjEtMTEuNS04Mi42LTM3LjUtODMtMzcuOGMtNi4xLTQuMy0xNC41LTIuOC0xOC44LDMuM2MtNC4zLDYuMS0yLjgsMTQuNSwzLjMsMTguOGMxLjcsMS4yLDQxLjUsMjguOSw5MS4zLDQxLjcgICAgYzIzLjMsOC4zLDI1LjksMzMuMiwyNi42LDU2YzAsMC45LDAsMS43LDAuMSwyLjVjMC4xLDktMC41LDIyLjktMi4xLDMwLjljLTE2LjIsOS4yLTc5LjcsNDEtMTc2LjMsNDEgICAgYy05Ni4yLDAtMTYwLjEtMzEuOS0xNzYuNC00MS4xYy0xLjYtOC0yLjMtMjEuOS0yLjEtMzAuOWMwLTAuOCwwLjEtMS42LDAuMS0yLjVjMC43LTIyLjgsMy4zLTQ3LjcsMjYuNi01NiAgICBjNDkuOC0xMi44LDg5LjYtNDAuNiw5MS4zLTQxLjdjNi4xLTQuMyw3LjYtMTIuNywzLjMtMTguOGMtNC4zLTYuMS0xMi43LTcuNi0xOC44LTMuM2MtMC40LDAuMy0zNy43LDI2LjMtODMsMzcuOCAgICBjLTAuNCwwLjEtMC43LDAuMi0xLDAuM2MtNDMuNCwxNC45LTQ0LjcsNjEuMi00NS4zLDgwLjljMCwwLjksMCwxLjctMC4xLDIuNWMwLDAuMSwwLDAuMiwwLDAuM2MtMC4xLDUuMi0wLjIsMzEuOSw1LjEsNDUuMyAgICBjMSwyLjYsMi44LDQuOCw1LjIsNi4zYzMsMiw3NC45LDQ3LjgsMTk1LjIsNDcuOHMxOTIuMi00NS45LDE5NS4yLTQ3LjhjMi4zLTEuNSw0LjItMy43LDUuMi02LjMgICAgQzQ0Nyw0MTUuNSw0NDYuOSwzODguOCw0NDYuOCwzODMuNnoiIGZpbGw9IiMwMDAwMDAiLz4KCTwvZz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K" /> -->
        <img width="64" height="64" style="border-radius:50%;" src="https://res.cloudinary.com/dw7ckktut/image/upload/v1554643930/ramaiah.jpg" />
      </div>
    </div>
    <div class="todo-list">
      <div v-if="tasks.length > 0" class="">
        <ul id="tasks-list">
          <li class="task" v-for="(task, index) in tasks" :key="task.id" :index="index" contenteditable="true"  draggable="true" @dragstart="drag_start" @dragend="drag_end()" >
            <div style="padding: 7px 10px 10px 20px; font-weight: 550; opacity: 0.6; color: #111; font-size: 18px; font-family: Helvitica;"> {{task.text}} </div>
            <div style="padding: 2px 0px 0px 20px; opacity: 0.6; font-weight:550; color: #333;"> Due Fri Mar 12 </div>
          </li>
        </ul>
      </div>
    </div>

    <div class="stable-div">
      <img v-if="deleteIcon === true" title="drop a task here to delete" class="cursor" @drop="drop" @dragover="drag_over" width="74" height="72" src="https://cdn1.iconfinder.com/data/icons/round-ui/123/47-512.png" />
        <!-- &nbsp; &nbsp; -->
      <!-- <img  src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDQyIDQyIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA0MiA0MjsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+Cjxwb2x5Z29uIHBvaW50cz0iNDIsMTkgMjMsMTkgMjMsMCAxOSwwIDE5LDE5IDAsMTkgMCwyMyAxOSwyMyAxOSw0MiAyMyw0MiAyMywyMyA0MiwyMyAiIGZpbGw9IiMwMDAwMDAiLz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" /> -->
      <img v-if="deleteIcon === false" title="click to add net task" @click="addTask()" class="cursor" width="64" height="64" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDUwIDUwIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MCA1MDsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxjaXJjbGUgc3R5bGU9ImZpbGw6IzQzQjA1QzsiIGN4PSIyNSIgY3k9IjI1IiByPSIyNSIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIyNSIgeTE9IjEzIiB4Mj0iMjUiIHkyPSIzOCIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIzNy41IiB5MT0iMjUiIHgyPSIxMi41IiB5Mj0iMjUiLz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" />
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
      taskId: 0,
      deleteIcon: false
    }
  },
  methods: {
    addTask () {
      console.log('called add task')
      this.tasks.push({
        id: this.taskId,
        text: 'Task ' + (this.taskId + 1)
      })

      this.taskId++
    },
    drag_start (event) {
      this.deleteIcon = true
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
      this.deleteIcon = false
    },
    drag_end () {
      this.deleteIcon = false
    }
  }
}
</script>

<style>
.todo-list {
  /* text-align: center; */
  /* align-content: center; */
  overflow-y: auto;
  background-color: #fbfbfbaa;
  min-height: 77%;
  max-height: 77%;
  /* height: 50%; */
  width: 100%;
  position: absolute;
  overflow-y: auto;
}

.todo-list-main {
  width: 40%;
  /* align-content: center;
  text-align: center; */
  min-height: 100%;
  background-color: #fbfbfbaa;
  margin-top: -10px;
  position: absolute;
  box-shadow: 0 2px 5px 0.8px #bebebe;
  border-radius: 4px;
  margin-left: 30%;
}

ul > li {
  list-style: none;
  padding: 13px 13px 13px 0px;
  margin-top: 10px;
  /* margin-left: -4%; */
  margin-bottom: 10px;
  width: 90%;
  background-color: #fefefeca;
  border-radius: 6px;
  box-shadow: 0 1px 2px 0.2px #c9c9c9
}

.task:hover {
  cursor: pointer;
}

.task:focus {
  cursor: text;
}

.user-logo-main {
  /* margin-top: 20px; */
  /* text-align: center; */
  /* align-content: center; */
  background-color: #fcfcfcaa;
  padding: 20px 0px 20px 0px;
  width: 100%;
  min-width: 100%;
  display: flex;
}

.user-logo-details-main {
  margin-left: 4%;
  margin-top: 2%;
  padding: 15px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
}

.user-logo-details1 {
  /* margin-left: 1%; */
  /* padding: 5px; */
  font-weight: 550;
  font-size: 22px;
  font-family: sans-serif;
}

.user-logo-details2 {
  /* margin-left: 1%; */
  padding: 5px 5px 5px 0px;
  font-weight: 550;
  font-size: 17px;
  opacity: 0.6;
  margin-top: 1.3%;
  color: #333;
  /* font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif */
}

.user-logo {
  margin-top: 3.5%;
  margin-left: 6%;
  /* padding: 5px; */
  /* margin-top: 1.3%; */
}

.cursor:hover {
  cursor: pointer;
}

.stable-div {
  margin-top: 50px !important;
  position: absolute;
  /* right: 0; */
  bottom: 0;
  text-align: center;
  align-content: center;
  padding: 20px 0px 20px 0px;
  width: 100%;
  /* background-color: #fafafaaa; */
}
</style>
