<template>
  <div>
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
    <img src="../assets/img.png" alt="">
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
  width: auto;
  height: 500px;
  background-color: #3c474b;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

.bar {
  --height: 250px;
  width: 50px;
  background-color: #993f3f;
  margin: auto auto 0;
  height: calc(var(--height) / 50 * 500);
  transition: height .5s;
}

.bar:nth-child(1) {
  background-color: #c3e3ca;
}
.bar:nth-child(2) {
  background-color: #fccdc0;
}
.bar:nth-child(3) {
  background-color: #b6d9ef;
}
.bar:nth-child(4) {
  background-color: #ffe6b0;
}

.category {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  padding-top: 4px;
}

.category div {
  text-align: center;
}

img {
  width: 100%;
  height: auto;
}
</style>
