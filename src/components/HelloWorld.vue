<template>
  <div class="task-container">

    <div class="container">
      <div class="row justify-content-md-center">
        <div
          class="col-auto"
          style="background: #ffffff"
        >
          <div style="width: 600px; height: 500px">
            <p class="title">My task</p>

            <!-- Input -->
            <div class="d-flex" style="margin-top: 16px">
              <input v-model="task"
                type="text"
                placeholder="Enter your task description"
                class="form-control"
              />
              <button class="btn btn-warning rounded-0" @click="submitTask()" style="margin-left: 8px" v-if="!editedTaskIndex">Submit</button>
              <button class="btn btn-warning rounded-0" @click="submitTask()" style="margin-left: 8px" v-if="editedTaskIndex">Update</button>
            </div>

            <!-- Task table -->
            <div class="table-content">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <th scope="col" class="text-center">Task</th>
                    <th scope="col" class="text-center">Status</th>
                    <th scope="col" class="text-center">Update</th>
                    <th scope="col" class="text-center">Remove</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(task,index) in tasks" :key="index">
                    <th scope="row">{{task.name}}</th>
                    <td class="pointer" >
                      {{task.status}}
                    </td>
                    <td>
                      <div class="text-center" @click="editTask(index)">
                        <span class="fa fa-pen"></span>
                      </div>
                    </td>
                    <td>
                      <div class="text-center" @click="removeTask(index)">
                        <span class="fa fa-trash"></span>
                      </div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      task : '',
      flag : true,
      editedTaskIndex : null,
      tasks : [
        {
          name : "The very first task",
          status : "in-progress"
        },
        {
          name : "The second task",
          status : "in-progress"
        }
      ]
    }
  },

  methods : {
    submitTask () {
      if (this.task.length != '') {
        if (this.editedTaskIndex != null) {
          this.tasks[this.editedTaskIndex].name = this.task;
          this.editedTaskIndex = null
        }
        else {
          this.tasks.push(
            {
              name: this.task,
              status: 'to-do'
            }
          )
        }
        this.task = '';
        console.log(this.tasks);
      }
    },
    removeTask(i) {
      console.log(i);
      this.tasks.splice(i);
    },
    editTask(i) {
      console.log(i);
      this.task = this.tasks[i].name;
      this.editedTaskIndex = i;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.task-container {
  min-height: 500px;
  background: #d9d9d9;
  padding: 16px 32px;

  .title {
    font-family: sans-serif;
    font-size: 22px;
    font-weight: 600;
    line-height: 32px;
  }

  .table-content {
    margin-top: 16px;
  }
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.pointer {
  cursor: pointer;
}

.inProgClass {
  background: yellow;
}
</style>
