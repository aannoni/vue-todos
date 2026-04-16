<script setup>
  const props = defineProps({
    todopropertyname: {
      type: Object,
      required: true,
    },
  });
</script>

<template>
  <li>
    <input type="checkbox" :checked="todopropertyname.isCompleted"/>
    <div class="todo">
      <input type="text" :value="todopropertyname.inputState" />
        <span>
          {{ todopropertyname.inputState }}
        </span>
    </div>
    <div class="todo-actions"></div>
  </li>
</template>

<style lang="scss" scoped>

</style>