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
        <template #item="{ element, index }">
          <div class="item">
            <span>{{ index + 1 }}</span>
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
}

.wrapper {
  display: flex;
  flex-direction: column;
  margin-right: 75px;
}

.draggable {
  margin-bottom: 25px;
  margin-right: 25px;
  padding: 15px;
  background-color: #f0e9e7;
  display: inline-block;
}

.item {
  width: 150px;
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
</style>
