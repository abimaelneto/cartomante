<template>
  <div class="container">
    <h3>TESTE</h3>
    <svg viewBox="0 0 960 300">
      <symbol id="s-text">
        <text text-anchor="middle" x="50%" y="80%">Mom Dináh</text>
      </symbol>
      <g class="g-ants">
        <use xlink:href="#s-text" class="text-copy"></use>
        <use xlink:href="#s-text" class="text-copy"></use>
        <use xlink:href="#s-text" class="text-copy"></use>
        <use xlink:href="#s-text" class="text-copy"></use>
        <use xlink:href="#s-text" class="text-copy"></use>
      </g>
    </svg>
  </div>
</template>

<style scoped>
h3 {
  font-family: "Montserrat";
  color: white;
}
svg {
  display: block;
  font: 10.5em "Montserrat";
  width: 600px;
  height: 300px;
  margin: 0 auto;
}

.text-copy {
  fill: none;
  stroke-dasharray: 6% 29%;
  stroke-width: 5px;
  stroke-dashoffset: 0%;
  animation: stroke-offset 5.5s infinite linear;
}

.text-copy:nth-child(1) {
  stroke: plum;
  animation-delay: -1;
}

.text-copy:nth-child(2) {
  stroke: rgb(180, 116, 180);
  animation-delay: -2s;
}

.text-copy:nth-child(4) {
  stroke: plum;
  animation-delay: -4s;
}

.text-copy:nth-child(5) {
  stroke: plum;
  animation-delay: -5s;
}

@keyframes stroke-offset {
  100% {
    stroke-dashoffset: -35%;
  }
}
</style>
