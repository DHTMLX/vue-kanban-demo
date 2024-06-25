<script>
import { Kanban, Toolbar } from "@dhx/trial-kanban";
import "@dhx/trial-kanban/dist/kanban.css";

export default {
  props: ["cards", "columns"],

  mounted() {
    this.kanban = new Kanban(this.$refs.kanban_container, {
      cards: this.cards,
      columns: this.columns,
      // other configuration properties
    });

    this.toolbar = new Toolbar(this.$refs.toolbar_container, {
      api: this.kanban.api
    });
  },

  unmounted() {
    this.kanban.destructor();
    this.toolbar.destructor();
  }
};
</script>

<template>
  <div class="component_container">
    <div ref="toolbar_container"></div>
    <div ref="kanban_container" style="height: calc(100% - 56px);"></div>
  </div>
</template>
