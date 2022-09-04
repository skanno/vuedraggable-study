<template>
  <div>
    <draggable v-model="data.list" item-key="no" handle=".handle" @start="drag" @end="drop" @change="change">
      <template v-slot:item="{ element }">
        <div class="drag-item">
          <div class="card text-white bg-primary mb-3" style="max-width: 18rem;">
            <div class="card-header handle">
              <i class='bi bi-arrows-move'></i>
              No.{{element.no}}
            </div>
            <div class="card-body">
              <h5 class="card-title">{{ element.title }}</h5>
              <p class="card-text">{{ element.body }}</p>
            </div>
          </div>
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
          no: 1,
          title: 'SUM',
          body: '数値を合計する',
        },
        {
          no: 2,
          title: 'SUMIF',
          body: '条件を指定して数値を合計する',
        },
        {
          no: 3,
          title: 'SUMIFS',
          body: '複数の条件を指定して数値を合計する',
        },
        {
          no: 4,
          title: 'SUBTOTAL',
          body: 'さまざまな集計値を求める',
        },
        {
          no: 5,
          title: 'AGGREGATE',
          body: 'さまざまな集計値を求める',
        },
        {
          no: 6,
          title: 'PRODUCT',
          body: '積を求める',
        },
        {
          no: 7,
          title: 'SUMPRODUCT',
          body: '配列要素の積を合計する',
        },
        {
          no: 8,
          title: 'SUMSQ',
          body: '平方和を求める',
        },
        {
          no: 9,
          title: 'SUMX2PY2',
          body: '2つの配列要素の平方和を合計する',
        },
        {
          no: 10,
          title: 'SUMX2MY2',
          body: '2つの配列要素の平方差を合計する',
        },
      ],
    });

    const drag = (event) => {
      console.log('ドラッグ');
    };

    const drop = (event) => {
      console.log('ドロップ');
    };

    const change = (event) => {
      console.log(`${event.moved.oldIndex} -> ${event.moved.newIndex}`);
      console.log(event.moved.element);
    };

    return {
      data,
      drag,
      drop,
      change
    };
  }
};
</script>

<style scoped>
</style>
