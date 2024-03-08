<script>
import Kanban from "./components/Kanban.vue";
import { getData } from "./data";

export default {
  components: { Kanban },
  data() {
    const { columns, cards } = getData();
    return { columns, cards };
  },
};
</script>

<template>
  <Kanban :columns="columns" :cards="cards" />
</template>
