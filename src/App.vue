<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" :showAddTask="showAddTask" title="Hello" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    
    <!-- データ配列を動的に取得(v-) データtasks：Tasks name props-->
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" /> 
    <!-- に）ここにデータが存在するので実際のメソッド名を記載 -->
  </div>
</template>

<script>
//1 babel使用時のローカル登録
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  //2↑<div>で使用するためregister
  components: {
    Header,
    Tasks,
    AddTask,
    
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]

    },
    deleteTask(id) {
      // console.log('ほげ', id)//データ渡ってるか確認
      //クリックされたid 以外のidのtaskを代入
      if(confirm('Are You Sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
      
    },
    toggleReminder(id) {
      // console.log(id)//task. は未定義なので使用不可
      this.tasks = this.tasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Job interview',
        day: 'March 2st at 4:30pm',
        reminder: false,
      },
      {
        id: 3,
        text: 'lunch with Mr.Ker',
        day: 'March 3st at 12:10pm',
        reminder: true,
      },
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  padding: 2px;
  max-width: 960px;
  border-style: solid;
  border-width: 2px;
  border-color: aqua;
}
.btn {
  padding: 10px;
  height: 40px;
  color: aliceblue;
}
</style>

