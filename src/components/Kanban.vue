<script>
import { Kanban, Toolbar } from "@dhx/trial-kanban";
import "@dhx/trial-kanban/dist/kanban.css";

export default {
  props: ["cards", "columns"],

  mounted() {
    const kanban = new Kanban(this.$refs.kanban_container, {
      cards: this.cards,
      columns: this.columns,
      // other configuration properties
    });

    new Toolbar(this.$refs.toolbar_container, {
      api: kanban.api
    });
  },

  unmounted() {
    this.$refs.toolbar_container.innerHTML = "";
    this.$refs.kanban_container.innerHTML = "";
  }
};
</script>

<template>
    <div ref="toolbar_container"></div>
    <div ref="kanban_container" style="width: 100%; height: 100%"></div>
</template>
