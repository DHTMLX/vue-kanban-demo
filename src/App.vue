<script>
import Kanban from "./components/Kanban.vue";
import { getData } from "./data";

export default {
  components: { Kanban },
  data() {
    const { columns, cards, rows, cardShape } = getData();
    return { columns, cards, rows, cardShape };
  }
};
</script>

<template>
  <Kanban :columns="columns" :cards="cards" :rows="rows" :cardShape="cardShape" />
</template>
