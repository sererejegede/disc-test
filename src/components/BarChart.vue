<template>
  <div style="position: fixed">
    <div class="chart">
      <div class="bar" :style="{ '--height': `${D}px` }"></div>
      <div class="bar" :style="{ '--height': `${I}px` }"></div>
      <div class="bar" :style="{ '--height': `${S}px` }"></div>
      <div class="bar" :style="{ '--height': `${C}px` }"></div>
    </div>
    <div class="category">
      <div>
        <b>D </b><span>({{ D }})</span>
      </div>
      <div>
        <b>I </b><span>({{ I }})</span>
      </div>
      <div>
        <b>S </b><span>({{ S }})</span>
      </div>
      <div>
        <b>C </b><span>({{ C }})</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    D: {
      type: [Number, String],
      required: true,
    },
    I: {
      type: [Number, String],
      required: true,
    },
    S: {
      type: [Number, String],
      required: true,
    },
    C: {
      type: [Number, String],
      required: true,
    },
  },
};
</script>

<style>
.chart {
  width: 500px;
  height: 500px;
  background-color: #f0e9e7;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

.bar {
  width: 50px;
  background-color: #993f3f;
  margin: auto auto 0;
  height: calc(var(--height) / 50 * 500);
  transition: height .5s;
}

.category {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  padding-top: 4px;
}

.category div {
  text-align: center;
}
</style>
