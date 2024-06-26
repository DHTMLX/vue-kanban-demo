<script>
import { Kanban, Toolbar, defaultEditorShape } from "@dhx/trial-kanban";
import "@dhx/trial-kanban/dist/kanban.css";

export default {
  props: ["cards", "columns", "rows", "cardShape"],

  mounted() {
    this.kanban = new Kanban(this.$refs.kanban_container, {
      cards: this.cards,
      columns: this.columns,
      rows: this.rows,
      rowKey: "type",
      cardShape: this.cardShape,
      editorShape: [
        ...defaultEditorShape, // import default config for editorShape
        {
          type: "links",
          key: "links",
          label: "Links"
        },
        {
          type: "comments",
          key: "comments",
          label: "Comments",
          config: {
            placement: "editor"
          }
        }
      ],
      currentUser: 1,
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
