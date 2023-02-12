<script setup>
import { store } from "./store.js";
import ActionButton from "./ActionButton.vue";
</script>

<template>
  <div
    class="modal"
    :class="{
      modalBlue: store.selected === 'blue',
      modalRed: store.selected === 'red',
      modalOrange: store.selected === 'orange',
      modalGreen: store.selected === 'green',
    }"
  >
    <div style="display: inline-block">
      <img
        v-if="store.selected === 'blue'"
        src="./icons/information.svg"
        width="27"
        height="27"
      />
      <img
        v-if="store.selected === 'red'"
        src="./icons/error.svg"
        width="27"
        height="27"
      />
      <img
        v-if="store.selected === 'orange'"
        src="./icons/warning.svg"
        width="27"
        height="27"
      />
      <img
        v-if="store.selected === 'green'"
        src="./icons/success.svg"
        width="27"
        height="27"
      />
    </div>
    <div style="margin-left: 10px; padding-right: 30px; width: 100%">
      <div
        v-if="
          store.modalType === 'all' ||
          store.modalType === 'title' ||
          store.modalType === 'titleContent'
        "
        class="title"
      >
        A short descriptive header
      </div>
      <div
        v-if="
          store.modalType === 'all' ||
          store.modalType === 'content' ||
          store.modalType === 'titleContent'
        "
        class="content"
      >
        This is a paragraph of information with additional supporting detail or
        links to help the user understand what they should do.
      </div>
      <div v-if="store.modalType === 'all'" class="buttons">
        <ActionButton
          buttonType="secondary"
          :noMargin="true"
          :buttonTheme="store.selected"
          style="margin-top: 10px"
        />
        <ActionButton
          buttonType="primary"
          :buttonTheme="store.selected"
          style="margin-top: 10px"
        />
      </div>
    </div>
    <img class="close" src="./icons/close.svg" width="13" height="13" />
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600;700&display=swap");

.modal {
  display: flex;
  width: 80%;
  height: fit-content;
  justify-content: space-between;
  border-radius: 5px;
  text-align: left;
  padding-top: 20px;
  padding-left: 30px;
  padding-right: 30px;
  padding-bottom: 20px;
}

.modalBlue {
  border: 1px solid rgb(44, 117, 221);
  background-color: rgb(244, 250, 255);
}

.modalRed {
  border: 1px solid rgb(204 49 35);
  background-color: rgb(254 245 245);
}

.modalOrange {
  border: 1px solid rgb(220 90 0);
  background-color: rgb(253 243 225);
}

.modalGreen {
  border: 1px solid rgb(0 135 0);
  background-color: rgb(248 255 242);
}

.title {
  font-weight: bold;
  display: inline-block;
}

.content {
  font-weight: 400;
}

.buttons {
  margin-top: 10px;
}

.close {
  cursor: pointer;
}
</style>
