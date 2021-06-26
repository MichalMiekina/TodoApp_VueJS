<template>
  <div id="nav">
    <input type="text" placeholder="Type new task..." v-model="newTask" />
    <button @click="handleButton">Add</button>

    <section>
      <h3>Tasks to do</h3>

      <div
        class="task"
        v-for="task in tasks"
        v-bind:key="task.id"
        v-bind:class="{
          completed: task.completed,
        }"
        @click="checkTask(task.id)"
      >
        <span>{{ task.name }}</span>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { name: "wash the dishes ", completed: false, id: "1" },
        { name: "vacuum ", completed: false, id: "2" },
        { name: "walk with a dog ", completed: false, id: "3" },
      ],
    };
  },
  methods: {
    handleButton() {
      if (this.newTask.length > 0) {
        this.tasks.push({
          name: this.newTask,
          completed: false,
          id: Math.random(),
        });
        this.newTask = "";
      }
    },
    checkTask(id) {
      const index = this.tasks.findIndex((el) => el.id === id);
      this.tasks[index].completed = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

*,
*::after,
*::before {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
}

#app {
  max-width: 500px;
  padding: 30px 0;
  margin: 0 auto;
  background-color: rgb(255, 150, 150);
}

h1 {
  text-align: center;
}

main {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

section {
  flex-basis: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  text-align: center;
}

section h3 {
  flex-basis: 100%;
}
.task {
  flex-basis: 100%;
  display: flex;
  justify-content: center;
}
.task span {
  width: 250px;
  padding: 20px 0;
  border: 1px solid red;
  margin-top: 10px;
  background-color: rgb(255, 100, 100);
}

.completed span {
  background-color: gray;
  text-decoration: line-through;
}
</style>
