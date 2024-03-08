<script>
import { Kanban } from "@dhx/trial-kanban";
import "@dhx/trial-kanban/dist/kanban.css";

export default {
  props: ["cards", "columns"],

  mounted() {
    new Kanban(this.$refs.cont, {
      cards: this.cards,
      columns: this.columns,
    });
  },
  unmounted() {
    this.$refs.cont.innerHTML = "";
  },
};
</script>

<template>
  <div ref="cont" style="width: 100%; height: 100%"></div>
</template>
