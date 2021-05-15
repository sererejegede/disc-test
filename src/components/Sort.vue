<template>
  <div class="container">
    <div class="wrapper">
      <draggable
        class="draggable"
        v-for="(item, key) in options"
        :key="key"
        v-model="item.option"
        ghost-class="ghost"
        animation="200"
        item-key="type"
      >
        <template #item="{ element }">
          <div class="item">
            {{ element.value }}
          </div>
        </template>
      </draggable>
    </div>
    <div>
      <bar-chart v-bind="disc" />
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import BarChart from "./BarChart.vue";
import options from "../options";

export default {
  components: { draggable, BarChart },
  data() {
    return {
      options,
    };
  },
  computed: {
    disc() {
      const res = {};
      const cumulative = [];
      this.options.forEach((item) => {
        item.option.forEach((l, i) => {
          cumulative.push({ [l.type]: 4 - i });
        });
        res.D = cumulative.filter((q) => q.D).reduce((a, c) => a + c.D, 0);
        res.I = cumulative.filter((q) => q.I).reduce((a, c) => a + c.I, 0);
        res.S = cumulative.filter((q) => q.S).reduce((a, c) => a + c.S, 0);
        res.C = cumulative.filter((q) => q.C).reduce((a, c) => a + c.C, 0);
      });
      return res;
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  max-width: 1280px;
  margin: 24px auto 0;
}

.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4px;
  margin-right: 10px;
}

.wrapper::-webkit-scrollbar {
  width: 10px;
}

.wrapper:hover::-webkit-scrollbar-track-piece {
  background-color: rgba(0, 0, 0, 0.05);
}

.wrapper:hover::-webkit-scrollbar-thumb {
  background-color: rgba(0, 0, 0, 0.15);
}

.draggable {
  padding: 15px;
  background-color: #f0e9e7;
  display: inline-block;
}

.item {
  /*width: 100%;*/
  padding: 8px;
  border: 1px solid;
  border-radius: 5px;
  cursor: move;
}

.item:not(:last-child) {
  margin-bottom: 4px;
}

.ghost {
  opacity: 0;
  /* background-color: #89ceac; */
}

@media screen and (max-width: 1024px) {
  .container {
    flex-wrap: wrap;
  }
}
</style>
