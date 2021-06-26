<template>
  <div
    class="task"
    v-bind:class="{completed: task.completed}"
    @click="checkTask(task.id)"
    >
    <span>{{ task.name }}</span>
  </div>
</template>

<script>
export default {
    props:['task'],
    methods: {
        checkTask(){
            this.$emit('checkClicked', this.task.id)
        }
    }
}
</script>

