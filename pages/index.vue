<template>
  <main>
    <h1>DAFTAR TUGAS</h1>
    <p>Tugas harian</p>
    <div class="create-new">
      <input 
      type="text"
      v-model="newTask"
      placeholder="Buat tugas baru"
      @keypress.enter="addTask" />
      <button @click="addTask">Buat</button>
    </div>

    <div class="tasks">
      <!--Component-->
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data() {
    return {
      newTask: ''
    }
  },
 
  methods : {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
