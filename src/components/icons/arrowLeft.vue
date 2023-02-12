<script setup>
const props = defineProps({
  buttonType: String,
  buttonTheme: String,
});
</script>

<template>
  <svg
    version="1.1"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    x="0px"
    y="0px"
    viewBox="0 0 499.32 375.23"
    style="enable-background: new 0 0 499.32 375.23"
    xml:space="preserve"
    class="arrow"
    :class="{
      white:
        (buttonTheme === 'red' ||
          buttonTheme === 'orange' ||
          buttonTheme === 'green') &&
        buttonType === 'primary',
      arrowBlue: buttonType === 'secondary' && buttonTheme === 'blue',
      arrowRed: buttonType === 'secondary' && buttonTheme === 'red',
      arrowOrange: buttonType === 'secondary' && buttonTheme === 'orange',
      arrowGreen: buttonType === 'secondary' && buttonTheme === 'green',
    }"
  >
    <g id="Layer_1"></g>
    <g id="Layer_2">
      <path
        d="M4.04,198.97c0.38,0.47,0.8,0.93,1.24,1.37l169.61,169.61c7.03,7.03,18.43,7.03,25.46,0c7.03-7.03,7.03-18.43,0-25.46
		L61.46,205.61h419.87c9.94,0,18-8.06,18-18s-8.06-18-18-18H61.46L200.34,30.73c7.03-7.03,7.03-18.43,0-25.46
		C196.83,1.76,192.22,0,187.61,0s-9.21,1.76-12.73,5.27L5.27,174.88C-1.32,181.47-1.73,191.9,4.04,198.97z"
      />
    </g>
  </svg>
</template>

<style scoped>
.arrow {
  height: 15px;
  margin: auto 5px;
  align-items: center;
}
.white {
  fill: #fff;
}

.arrowBlue {
  fill: rgb(199, 81, 0);
}

.arrowRed {
  fill: rgb(204, 49, 35);
}

.arrowOrange {
  fill: rgb(220, 90, 0);
}

.arrowGreen {
  fill: rgb(0, 135, 0);
}
</style>
