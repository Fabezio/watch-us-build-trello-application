<template lang="pug">
.board
  .flex.flex-row.items-start
    .column(v-for='(column, $columnIndex) of board.columns' :key='$columnIndex')
      .flex.items-center.mb-2.font-bold {{column.name}}
      .list-reset
        .task(v-for='(task, $taskIndex) of column.tasks' :key='taskIndex')
          // h5.w-full.flex-no-shrink {{task}}
          span.w-full.flex-no-shrink.font-bold {{task.name}}
          p.w-full.flex-no-shrink.mt-1.text-sm(v-if='task.description') {{task.description}}

</template>

<script>
import {mapState} from 'vuex'
export default {
  computed: mapState(['board'])
}
</script>

<style lang="css">
.task {
  @apply flex items-center flex-wrap shadow mb-2 py-2 px-2 rounded bg-white text-grey-darkest no-underline;
}

.column {
  @apply bg-grey-light p-2 mr-4 text-left shadow rounded;
  min-width: 350px;
}

.board {
  @apply p-4 bg-teal-dark h-full overflow-auto;
}

.task-bg {
  @apply pin absolute;
  background: rgba(0,0,0,0.5);
}
</style>
