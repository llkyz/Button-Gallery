<script setup>
import ArrowLeft from "./icons/arrowLeft.vue";
import ArrowRight from "./icons/arrowRight.vue";

const props = defineProps({
  buttonType: String,
  buttonTheme: { type: String, required: true },
  buttonStyle: { type: String, default: "all" },
  buttonLabel: { type: String, default: "Action" },
  arrow: { type: String, default: "none" },
  noMargin: { type: Boolean, default: false },
});
</script>

<template>
  <div
    class="button"
    :class="{
      primaryBlue: buttonType === 'primary' && buttonTheme === 'blue',
      primaryRed: buttonType === 'primary' && buttonTheme === 'red',
      primaryOrange: buttonType === 'primary' && buttonTheme === 'orange',
      primaryGreen: buttonType === 'primary' && buttonTheme === 'green',
      secondaryBlue: buttonType === 'secondary' && buttonTheme === 'blue',
      secondaryRed: buttonType === 'secondary' && buttonTheme === 'red',
      secondaryOrange: buttonType === 'secondary' && buttonTheme === 'orange',
      secondaryGreen: buttonType === 'secondary' && buttonTheme === 'green',
      expand: buttonStyle != 'icon',
    }"
    :style="[noMargin ? { marginLeft: 0 } : {}]"
  >
    <ArrowLeft
      class="arrow"
      v-if="
        (buttonStyle === 'all' || buttonStyle === 'icon') && arrow === 'left'
      "
      :buttonType="buttonType"
      :buttonTheme="buttonTheme"
    />
    <div
      class="buttonText"
      v-if="buttonStyle === 'all' || buttonStyle === 'text'"
    >
      {{ buttonLabel }}
    </div>
    <ArrowRight
      class="arrow"
      v-if="
        (buttonStyle === 'all' || buttonStyle === 'icon') && arrow === 'right'
      "
      :buttonType="buttonType"
      :buttonTheme="buttonTheme"
    />
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600;700&display=swap");

.button {
  display: inline-flex;
  vertical-align: top;
  width: fit-content;
  height: 42px;
  padding-left: 6px;
  padding-right: 6px;
  border-radius: 10px;
  cursor: pointer;
  margin: auto 5px;
}

.button:hover {
  box-shadow: 5px 5px 10px rgba(40, 40, 40, 0.3);
}

.button:active {
  box-shadow: inset 0px 0px 1px 2px black;
}

.expand {
  padding-left: 24px;
  padding-right: 24px;
}

.primaryBlue {
  background-color: rgb(247, 186, 80);
  color: rgb(12, 12, 12);
}

.primaryBlue:hover {
  background-color: rgb(245, 171, 43);
}

.primaryRed {
  background-color: rgb(204, 49, 35);
  color: rgb(255, 255, 255);
}

.primaryRed:hover {
  background-color: rgb(168, 43, 31);
}
.primaryOrange {
  background-color: rgb(220, 90, 0);
  color: rgb(255, 255, 255);
}

.primaryOrange:hover {
  background-color: rgb(196, 83, 2);
}

.primaryGreen {
  background-color: rgb(0, 135, 0);
  color: rgb(255, 255, 255);
}

.primaryGreen:hover {
  background-color: rgb(0, 110, 0);
}

.secondaryBlue {
  border: 1px solid rgb(199, 81, 0);
  color: rgb(199, 81, 0);
}

.secondaryRed {
  border: 1px solid rgb(204 49 35);
  color: rgb(204 49 35);
}

.secondaryOrange {
  border: 1px solid rgb(220 90 0);
  color: rgb(220 90 0);
}

.secondaryGreen {
  border: 1px solid rgb(0 135 0);
  color: rgb(0 135 0);
}
.buttonText {
  margin: auto 5px;
  font-family: "Open Sans";
  font-size: 16px;
  font-weight: 600;
}
</style>
