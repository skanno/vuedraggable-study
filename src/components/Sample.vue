<template>
  <div class="hello">
    <draggable v-model="data.list" item-key="id" handle=".handle">
      <template #item="{element}">
        <div class="drag-item">
          <span class="handle">ハンドル</span>
          {{ element.id }}{{ element.content }}
        </div>
      </template>
    </draggable>
  </div>
</template>

<script>
import { reactive } from 'vue';
import draggable from 'vuedraggable';

export default {
  components: {
    draggable,
  },
  setup(props) {
    const data = reactive({
      list: [
        {
          id: 1,
          content: "あいうえお",
        },
        {
          id: 2,
          content: "かきくけこ",
        },
        {
          id: 3,
          content: "さしすせそ",
        },
      ],
    });

    return {data};
  }
};
</script>

<style scoped>
.drag-item {
  background: rgb(233, 249, 255);
  margin: 10px 0;
}
</style>