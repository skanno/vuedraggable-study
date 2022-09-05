<template>
  <div class="row">
    <draggable class="col-3" group="list" v-model="data.list1" item-key="no" handle=".handle" @start="drag" @end="drop" @change="change($event, '左')">
      <template v-slot:item="{ element }">
        <div class="drag-item">
          <div v-bind:class="{card: true, 'text-white': true, 'mb-3': true, 'bg-primary': element.primary, 'bg-secondary': !element.primary}" style="max-width: 18rem;">
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

    <draggable class="col-3" group="list" v-model="data.list2" item-key="no" handle=".handle" @start="drag" @end="drop" @change="change($event, '右')">
      <template v-slot:item="{ element }">
        <div class="drag-item">
          <div v-bind:class="{card: true, 'text-white': true, 'mb-3': true,  'bg-primary': element.primary, 'bg-secondary': !element.primary}"  style="max-width: 18rem;">
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
import { createToaster } from "@meforma/vue-toaster";

const toaster = createToaster({
  position: 'top',
  duration: 3000
});

export default {
  components: {
    draggable,
  },
  setup(props) {
    const data = reactive({
      list1: [
        {
          no: 1,
          title: 'SUM',
          body: '数値を合計する',
          primary: true
        },
        {
          no: 2,
          title: 'SUMIF',
          body: '条件を指定して数値を合計する',
          primary: true
        },
        {
          no: 3,
          title: 'SUMIFS',
          body: '複数の条件を指定して数値を合計する',
          primary: true
        },
        {
          no: 4,
          title: 'SUBTOTAL',
          body: 'さまざまな集計値を求める',
          primary: true
        },
        {
          no: 5,
          title: 'AGGREGATE',
          body: 'さまざまな集計値を求める',
          primary: true
        },
      ],
      list2: [
        {
          no: 6,
          title: 'PRODUCT',
          body: '積を求める',
          primary: false
        },
        {
          no: 7,
          title: 'SUMPRODUCT',
          body: '配列要素の積を合計する',
          primary: false
        },
        {
          no: 8,
          title: 'SUMSQ',
          body: '平方和を求める',
          primary: false
        },
        {
          no: 9,
          title: 'SUMX2PY2',
          body: '2つの配列要素の平方和を合計する',
          primary: false
        },
        {
          no: 10,
          title: 'SUMX2MY2',
          body: '2つの配列要素の平方差を合計する',
          primary: false
        },
      ],
      list3: [
        {
          no: 6,
          title: 'PRODUCT',
          body: '積を求める',
          primary: false
        },
        {
          no: 7,
          title: 'SUMPRODUCT',
          body: '配列要素の積を合計する',
          primary: false
        },
        {
          no: 8,
          title: 'SUMSQ',
          body: '平方和を求める',
          primary: false
        },
        {
          no: 9,
          title: 'SUMX2PY2',
          body: '2つの配列要素の平方和を合計する',
          primary: false
        },
        {
          no: 10,
          title: 'SUMX2MY2',
          body: '2つの配列要素の平方差を合計する',
          primary: false
        },
      ],
    });

    const drag = (event) => {
      // console.log('ドラッグ');
    };

    const drop = (event) => {
      // console.log('ドロップ');
    };

    const change = (event, type) => {
      if (event.moved) {
        toaster.info(`「${event.moved.element.title}」が移動しました。`);
      }

      if (event.added) {
        toaster.info(`${type}へ「${event.added.element.title}」を追加しました。`);
      }

      if (event.removed) {
        toaster.info(`${type}から「${event.removed.element.title}」を削除しました。`);
      }
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
