<template>
    <div class="hello">
        <draggable v-model="data" group="people" item-key="id" handle=".handle">
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
import draggable from "vuedraggable";

export default {
    components: {
        draggable,
    },
    data() {
        return {
            data: [
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
        };
    },
};
</script>
