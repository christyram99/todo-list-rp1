<template>
  <div v-if="displayModel" id="myModal" class="modal" :class="{block: displayModel}">
     <div class="modal-content">
      <div class="modal-header">
        <span @click="closeModel()" class="close">&times;</span>
        <h2>&nbsp;</h2>
      </div>
      <div class="modal-body">
        <textarea v-model="taskData" rows="7" resize="none" placeholder="What do you like to add" style="font-size: 14px; padding: 10px 10px 10px 10px; width: 95%; border:none;" >
        </textarea>
        <div style="right:15px; margin-top: -20px; position: absolute; float:right; margin-bottom:3px;">
          <!-- <datepicker>
            <img class="cursor" width="16" height="16" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIj8+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiBoZWlnaHQ9IjUxMnB4IiB2aWV3Qm94PSIwIDAgNTEyIDUxMiIgd2lkdGg9IjUxMnB4Ij48cGF0aCBkPSJtNDgyIDI5Mi4yNXYtMjQ2LjI1YzAtOC4yODUxNTYtNi43MTQ4NDQtMTUtMTUtMTVoLTc2di0xNmMwLTguMjg1MTU2LTYuNzE0ODQ0LTE1LTE1LTE1cy0xNSA2LjcxNDg0NC0xNSAxNXYxNmgtNjB2LTE2YzAtOC4yODUxNTYtNi43MTQ4NDQtMTUtMTUtMTVzLTE1IDYuNzE0ODQ0LTE1IDE1djE2aC02MHYtMTZjMC04LjI4NTE1Ni02LjcxNDg0NC0xNS0xNS0xNXMtMTUgNi43MTQ4NDQtMTUgMTV2MTZoLTYwdi0xNmMwLTguMjg1MTU2LTYuNzE0ODQ0LTE1LTE1LTE1cy0xNSA2LjcxNDg0NC0xNSAxNXYxNmgtNzZjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTV2MzkxYzAgOC4yODUxNTYgNi43MTQ4NDQgMTUgMTUgMTVoMjQ5LjgwNDY4OGMyNC4yNSAzNi4xNTIzNDQgNjUuNDg4MjgxIDYwIDExMi4xOTUzMTIgNjAgNzQuNDM3NSAwIDEzNS02MC41NjI1IDEzNS0xMzUgMC0zMi4wNzAzMTItMTEuMjUtNjEuNTYyNS0zMC04NC43NXptLTM5MS0yMzEuMjV2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjF2NjBoLTQyMnYtNjB6bS02MSAzNjF2LTI3MWg0MjJ2MTEzLjgwNDY4OGMtMjEuNDY0ODQ0LTE0LjM5NDUzMi00Ny4yNjk1MzEtMjIuODA0Njg4LTc1LTIyLjgwNDY4OC00Ny4zOTg0MzggMC04OS4xNjQwNjIgMjQuNTU4NTk0LTExMy4yNTc4MTIgNjEuNjEzMjgxLTIuMDI3MzQ0LTEuMDIzNDM3LTQuMzEyNS0xLjYxMzI4MS02Ljc0MjE4OC0xLjYxMzI4MWgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTVoMjIuNzIyNjU2Yy0zLjM4NjcxOCA5LjU1NDY4OC01LjczMDQ2OCAxOS42MDE1NjItNi44ODI4MTIgMzBoLTE1LjgzOTg0NGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgxNS44Mzk4NDRjMS4xNTIzNDQgMTAuMzk4NDM4IDMuNDkyMTg3IDIwLjQ0NTMxMiA2Ljg4MjgxMiAzMHptMzQ3IDYwYy01Ny44OTg0MzggMC0xMDUtNDcuMTAxNTYyLTEwNS0xMDVzNDcuMTAxNTYyLTEwNSAxMDUtMTA1IDEwNSA0Ny4xMDE1NjIgMTA1IDEwNS00Ny4xMDE1NjIgMTA1LTEwNSAxMDV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im00MzcgMzYyaC00NXYtNDVjMC04LjI4NTE1Ni02LjcxNDg0NC0xNS0xNS0xNXMtMTUgNi43MTQ4NDQtMTUgMTV2NjBjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNWg2MGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTEzNiAxODJoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1aDMwYzguMjg1MTU2IDAgMTUtNi43MTQ4NDQgMTUtMTVzLTYuNzE0ODQ0LTE1LTE1LTE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48cGF0aCBkPSJtMTM2IDI0MmgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTVoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im0xMzYgMzAyaC0zMGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTIyNyAyMTJoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTVoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48cGF0aCBkPSJtMjI3IDI3MmgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNWgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im0xMzYgMzYyaC0zMGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTM0NyAyMTJoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTVoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48L3N2Zz4K" />
          </datepicker> -->
          <datepicker v-model="taskDate" @selected="doSomethingInParentComponentFunction" @opened="datepickerOpenedFunction" @closed="datepickerClosedFunction">
            <!-- <img class="cursor" width="16" height="16" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIj8+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiBoZWlnaHQ9IjUxMnB4IiB2aWV3Qm94PSIwIDAgNTEyIDUxMiIgd2lkdGg9IjUxMnB4Ij48cGF0aCBkPSJtNDgyIDI5Mi4yNXYtMjQ2LjI1YzAtOC4yODUxNTYtNi43MTQ4NDQtMTUtMTUtMTVoLTc2di0xNmMwLTguMjg1MTU2LTYuNzE0ODQ0LTE1LTE1LTE1cy0xNSA2LjcxNDg0NC0xNSAxNXYxNmgtNjB2LTE2YzAtOC4yODUxNTYtNi43MTQ4NDQtMTUtMTUtMTVzLTE1IDYuNzE0ODQ0LTE1IDE1djE2aC02MHYtMTZjMC04LjI4NTE1Ni02LjcxNDg0NC0xNS0xNS0xNXMtMTUgNi43MTQ4NDQtMTUgMTV2MTZoLTYwdi0xNmMwLTguMjg1MTU2LTYuNzE0ODQ0LTE1LTE1LTE1cy0xNSA2LjcxNDg0NC0xNSAxNXYxNmgtNzZjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTV2MzkxYzAgOC4yODUxNTYgNi43MTQ4NDQgMTUgMTUgMTVoMjQ5LjgwNDY4OGMyNC4yNSAzNi4xNTIzNDQgNjUuNDg4MjgxIDYwIDExMi4xOTUzMTIgNjAgNzQuNDM3NSAwIDEzNS02MC41NjI1IDEzNS0xMzUgMC0zMi4wNzAzMTItMTEuMjUtNjEuNTYyNS0zMC04NC43NXptLTM5MS0yMzEuMjV2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjB2MTVjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNXMxNS02LjcxNDg0NCAxNS0xNXYtMTVoNjF2NjBoLTQyMnYtNjB6bS02MSAzNjF2LTI3MWg0MjJ2MTEzLjgwNDY4OGMtMjEuNDY0ODQ0LTE0LjM5NDUzMi00Ny4yNjk1MzEtMjIuODA0Njg4LTc1LTIyLjgwNDY4OC00Ny4zOTg0MzggMC04OS4xNjQwNjIgMjQuNTU4NTk0LTExMy4yNTc4MTIgNjEuNjEzMjgxLTIuMDI3MzQ0LTEuMDIzNDM3LTQuMzEyNS0xLjYxMzI4MS02Ljc0MjE4OC0xLjYxMzI4MWgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTVoMjIuNzIyNjU2Yy0zLjM4NjcxOCA5LjU1NDY4OC01LjczMDQ2OCAxOS42MDE1NjItNi44ODI4MTIgMzBoLTE1LjgzOTg0NGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgxNS44Mzk4NDRjMS4xNTIzNDQgMTAuMzk4NDM4IDMuNDkyMTg3IDIwLjQ0NTMxMiA2Ljg4MjgxMiAzMHptMzQ3IDYwYy01Ny44OTg0MzggMC0xMDUtNDcuMTAxNTYyLTEwNS0xMDVzNDcuMTAxNTYyLTEwNSAxMDUtMTA1IDEwNSA0Ny4xMDE1NjIgMTA1IDEwNS00Ny4xMDE1NjIgMTA1LTEwNSAxMDV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im00MzcgMzYyaC00NXYtNDVjMC04LjI4NTE1Ni02LjcxNDg0NC0xNS0xNS0xNXMtMTUgNi43MTQ4NDQtMTUgMTV2NjBjMCA4LjI4NTE1NiA2LjcxNDg0NCAxNSAxNSAxNWg2MGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTEzNiAxODJoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1aDMwYzguMjg1MTU2IDAgMTUtNi43MTQ4NDQgMTUtMTVzLTYuNzE0ODQ0LTE1LTE1LTE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48cGF0aCBkPSJtMTM2IDI0MmgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTVoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im0xMzYgMzAyaC0zMGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTIyNyAyMTJoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTVoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48cGF0aCBkPSJtMjI3IDI3MmgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNWgtMzBjLTguMjg1MTU2IDAtMTUgNi43MTQ4NDQtMTUgMTVzNi43MTQ4NDQgMTUgMTUgMTV6bTAgMCIgZmlsbD0iIzAwMDAwMCIvPjxwYXRoIGQ9Im0xMzYgMzYyaC0zMGMtOC4yODUxNTYgMC0xNSA2LjcxNDg0NC0xNSAxNXM2LjcxNDg0NCAxNSAxNSAxNWgzMGM4LjI4NTE1NiAwIDE1LTYuNzE0ODQ0IDE1LTE1cy02LjcxNDg0NC0xNS0xNS0xNXptMCAwIiBmaWxsPSIjMDAwMDAwIi8+PHBhdGggZD0ibTM0NyAyMTJoMzBjOC4yODUxNTYgMCAxNS02LjcxNDg0NCAxNS0xNXMtNi43MTQ4NDQtMTUtMTUtMTVoLTMwYy04LjI4NTE1NiAwLTE1IDYuNzE0ODQ0LTE1IDE1czYuNzE0ODQ0IDE1IDE1IDE1em0wIDAiIGZpbGw9IiMwMDAwMDAiLz48L3N2Zz4K" /> -->
          </datepicker>
        </div>
      </div>
      <div class="modal-footer cursor" >
        <button :disabled="!taskData || !taskDate" :class="{disabled : (!taskData || !taskDate), cursor: (taskData && taskDate)}" @click=addTask2() style="width:100%; padding: 12px; background-color: #428bca; border: none; font-size:20px; color: white;"> + </button>
      </div>
    </div>
  </div>
  <div v-else class="todo-list-main">

    <div class="user-logo-main">
      <div class="user-logo-details-main" style="width: 90%">
        <div class="user-logo-details1">
          Hello Floyd Mullins
        </div>
        <div class="user-logo-details2">
          <div class="">
            You have {{tasks.length}} task(s)
          </div>
        </div>
      </div>
      <div class="user-logo" >
        <img width="64" height="64" style="border-radius:50%;" src="https://res.cloudinary.com/dw7ckktut/image/upload/v1554643930/ramaiah.jpg" />
      </div>
    </div>
    <div class="todo-list">
      <div v-if="tasks.length > 0" class="">
        <div class="task-l">
          <div class="task" v-for="(task, index) in tasks" :key="task.id" :data-index="index"  draggable="true" @dragstart="drag_start" >
            <div style="padding: 7px 10px 10px 20px; font-weight: 550; opacity: 0.9; color: #444; font-size: 15px; font-family: Sans-serif; display: flex">
              <div class="" style="width:97%"> {{task.text}} </div>
              <div class="" style="width:3%">
                <img width="16" height="16" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTYuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjUxMnB4IiBoZWlnaHQ9IjUxMnB4IiB2aWV3Qm94PSIwIDAgNTE1LjEgNTE1LjEiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDUxNS4xIDUxNS4xOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+CjxnPgoJPGcgaWQ9ImFjY2Vzcy1hbGFybXMiPgoJCTxwYXRoIGQ9Ik01MTIuNTUsOTkuNDVMMzk1LjI1LDBMMzYyLjEsMzguMjVsMTE3LjMsOTkuNDVMNTEyLjU1LDk5LjQ1eiBNMTUzLDQwLjhMMTE5Ljg1LDIuNTVMMi41NSw5OS40NUwzNS43LDEzNy43TDE1Myw0MC44eiAgICAgTTI3MC4zLDE1OC4xaC0zOC4yNXYxNTNsMTE5Ljg1LDczLjk1MWwyMC40LTMwLjYwMmwtMTAyLTYxLjE5OVYxNTguMXogTTI1Ny41NSw1Ni4xYy0xMjcuNSwwLTIyOS41LDEwMi0yMjkuNSwyMjkuNSAgICBjMCwxMjcuNSwxMDIsMjI5LjUsMjI5LjUsMjI5LjVzMjI5LjUtMTAyLDIyOS41LTIyOS41QzQ4Ny4wNSwxNTguMSwzODUuMDUsNTYuMSwyNTcuNTUsNTYuMXogTTI1Ny41NSw0NjQuMSAgICBjLTk5LjQ1LDAtMTc4LjUtNzkuMDQ5LTE3OC41LTE3OC41YzAtOTkuNDUsNzkuMDUtMTc4LjUsMTc4LjUtMTc4LjVzMTc4LjUsNzkuMDUsMTc4LjUsMTc4LjUgICAgQzQzNi4wNSwzODUuMDUxLDM1Nyw0NjQuMSwyNTcuNTUsNDY0LjF6IiBmaWxsPSIjMDAwMDAwIi8+Cgk8L2c+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" />
              </div>
            </div>
            <div style="padding: 2px 0px 0px 20px; opacity: 0.9; font-weight:550; color: #bbb; font-size:14px;"> Due {{frontEndDateFormat(task.date)}} </div>
          </div>
        </div>
      </div>
    </div>
    <div class="stable-div" @dragover="drag_over">
      <div align="center" @drop="drop" @dragover="drag_over" style="width: 100%; align: center; text-aling: center; align-content: center;"><img v-if="dragging === true" title="drop a task here to delete" class="cursor" width="74" height="72" src="https://cdn1.iconfinder.com/data/icons/round-ui/123/47-512.png" /></div>
      <img v-if="dragging === false" title="click to add net task" @click="openModel()" class="cursor" width="64" height="64" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgdmlld0JveD0iMCAwIDUwIDUwIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MCA1MDsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxjaXJjbGUgc3R5bGU9ImZpbGw6IzQzQjA1QzsiIGN4PSIyNSIgY3k9IjI1IiByPSIyNSIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIyNSIgeTE9IjEzIiB4Mj0iMjUiIHkyPSIzOCIvPgo8bGluZSBzdHlsZT0iZmlsbDpub25lO3N0cm9rZTojRkZGRkZGO3N0cm9rZS13aWR0aDoyO3N0cm9rZS1saW5lY2FwOnJvdW5kO3N0cm9rZS1saW5lam9pbjpyb3VuZDtzdHJva2UtbWl0ZXJsaW1pdDoxMDsiIHgxPSIzNy41IiB5MT0iMjUiIHgyPSIxMi41IiB5Mj0iMjUiLz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPGc+CjwvZz4KPC9zdmc+Cg==" />
    </div>
  </div>
</template>

<script>
import Datepicker from 'vuejs-datepicker'
export default {
  components: {
    Datepicker
  },
  name: 'SampleDiv',
  data () {
    return {
      msg: 'Sample Div',
      tasks: [],
      taskId: 0,
      dragging: false,
      displayModel: false,
      taskData: '',
      taskDate: new Date(),
      days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
      months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
      dragIndex: 0
    }
  },
  methods: {
    addTask2 () {
      this.tasks.push({
        id: this.taskId,
        text: this.taskData,
        date: this.taskDate
      })
      this.taskData = ''
      this.displayModel = false
      this.taskId++
    },
    drag_start (event) {
      this.dragging = true
      event.dataTransfer.setData('text', event.target.getAttribute('data-index'))
    },
    drag_over (event) {
      event.preventDefault()
    },
    drop (event) {
      event.preventDefault()
      var index = event.dataTransfer.getData('text')
      this.tasks.splice(index, 1)
      this.dragging = false
    },
    openModel () {
      this.displayModel = true
    },
    closeModel () {
      this.displayModel = false
    },
    doSomethingInParentComponentFunction () {
      console.log('doSomethingInParentComponentFunction called')
    },
    datepickerOpenedFunction () {
      console.log('datepickerOpenedFunction called')
    },
    datepickerClosedFunction () {
      console.log('datepickerClosedFunction called')
    },
    frontEndDateFormat (date) {
      let nDate = new Date(date)
      return this.days[nDate.getDay()] + ' ' + this.months[nDate.getMonth()] + ' ' + nDate.getDate()
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
  font-family: Arial, Helvetica, sans-serif;
}

.todo-list-main {
  width: 100%;
  margin-left: -8px;
  /* align-content: center;
  text-align: center; */
  min-height: 100%;
  background-color: #fbfbfbaa;
  margin-top: -10px;
  position: absolute;
  /* box-shadow: 0 2px 5px 0.8px #bebebe;
  border-radius: 4px; */
}

.task-l > div {
  margin-left: 4%;
  list-style: none;
  padding: 10px 0px 20px 0px;
  margin-top: 10px;
  margin-bottom: 15px;
  width: 92%;
  background-color: #fefefedd;
  border-radius: 4px;
  box-shadow: 0 1px 0px 0.3px #e7e7e7ee;
  font-size: 14px;
}

.task {
  /* padding: 10px; */
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
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
}

.user-logo-details1 {
  /* margin-left: 1%; */
  /* padding: 5px; */
  font-weight: 550;
  font-size: 18px;
  font-family: sans-serif;
}

.user-logo-details2 {
  /* margin-left: 1%; */
  padding: 20px 0px 5px 0px;
  font-weight: 550;
  font-size: 16px;
  opacity: 0.6;
  /* margin-top: 2%; */
  color: #333;
  /* font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif */
}

.user-logo {
  margin-top: 2%;
  margin-right: 2.5%;
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

/* The Modal (background) */
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
  /* margin-left: 1%; */
}

/* Modal Content */
.modal-content {
  position: relative;
  background-color: #fefefe;
  margin: auto;
  padding: 0;
  border: 1px solid #888;
  width: 80%;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.19);
  -webkit-animation-name: animatetop;
  -webkit-animation-duration: 0.4s;
  animation-name: animatetop;
  animation-duration: 0.4s
}

/* Add Animation */
@-webkit-keyframes animatetop {
  from {top:-300px; opacity:0};
  to {top:0; opacity:1}
}

@keyframes animatetop {
  from {top:-300px; opacity:0}
  to {top:0; opacity:1}
}

/* The Close Button */
.close {
  color: black;
  float: left;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}

.modal-header {
  padding: 5px 5px 0px 10px;
  /* background-color: #5cb85c; */
  color: white;
}

.modal-body {
  padding: 0px 10px 10px 10px;
  margin-top: -20px;
}

.modal-footer {
  padding: 2px 16px;
  background-color: #428bca;
  color: white;
}

.block {
  display: block;
}

textarea {
  resize: none;
}

textarea:focus {
  border: none;
  outline: none;
}

textarea:active{
  border: none;
  outline: none;
}

textarea:checked{
  border: none;
  outline: none;
}

.disabled {
  cursor: not-allowed;
}

.disabled:hover {
  cursor: not-allowed;
}
</style>
