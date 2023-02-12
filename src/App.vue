<script setup>
import ActionButton from "./components/ActionButton.vue";
import PreviewButton from "./components/PreviewButton.vue";
import Modal from "./components/Modal.vue";
import { store } from "./components/store.js";
</script>

<script>
export default {
  methods: {
    swapTheme(colour) {
      store.theme = colour;
    },
    modalTypeLeft() {
      if (store.modalType === "all") {
        store.modalType = "title";
      } else if (store.modalType === "title") {
        store.modalType = "titleContent";
      } else if (store.modalType === "titleContent") {
        store.modalType = "content";
      } else {
        store.modalType = "all";
      }
    },
    modalTypeRight() {
      if (store.modalType === "all") {
        store.modalType = "content";
      } else if (store.modalType === "content") {
        store.modalType = "titleContent";
      } else if (store.modalType === "titleContent") {
        store.modalType = "title";
      } else {
        store.modalType = "all";
      }
    },
    alertTypeLeft() {
      if (store.selected === "blue") {
        store.selected = "red";
      } else if (store.selected === "red") {
        store.selected = "orange";
      } else if (store.selected === "orange") {
        store.selected = "green";
      } else {
        store.selected = "blue";
      }
    },
    alertTypeRight() {
      if (store.selected === "blue") {
        store.selected = "green";
      } else if (store.selected === "green") {
        store.selected = "orange";
      } else if (store.selected === "orange") {
        store.selected = "red";
      } else {
        store.selected = "blue";
      }
    },
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div style="text-align: center; height: fit-content">
    <div>
      <h1>Gallery</h1>
      <div
        class="colourContainer"
        style="background-color: rgb(44, 117, 221)"
        @click="swapTheme('blue')"
      ></div>
      <div
        class="colourContainer"
        style="background-color: rgb(204, 49, 35)"
        @click="swapTheme('red')"
      ></div>
      <div
        class="colourContainer"
        style="background-color: rgb(220, 90, 0)"
        @click="swapTheme('orange')"
      ></div>
      <div
        class="colourContainer"
        style="background-color: rgb(0, 135, 0)"
        @click="swapTheme('green')"
      ></div>
    </div>
    <div
      style="
        width: fit-content;
        display: flex;
        justify-content: space-between;
        margin: 0 auto;
        margin-bottom: 10px;
      "
    >
      <PreviewButton buttonType="primary" arrow="left" />
      <PreviewButton buttonType="primary" />
      <PreviewButton buttonType="primary" arrow="right" />
    </div>
    <div
      style="
        width: fit-content;
        display: flex;
        justify-content: space-between;
        margin: 0 auto;
      "
    >
      <PreviewButton buttonType="secondary" arrow="left" />
      <PreviewButton buttonType="secondary" />
      <PreviewButton buttonType="secondary" arrow="right" />
    </div>
    <div
      style="
        margin-top: 20px;
        width: 100%;
        height: 2px;
        background-color: black;
      "
    ></div>
    <h1 style="margin: 10px auto">
      Select Alert ({{
        store.selected === "blue"
          ? "Information"
          : store.selected === "red"
          ? "Error"
          : store.selected === "orange"
          ? "Warning"
          : store.selected === "green"
          ? "Success"
          : ""
      }}:
      {{
        store.modalType === "all"
          ? "All"
          : store.modalType === "title"
          ? "Title Only"
          : store.modalType === "titleContent"
          ? "Title & Content"
          : store.modalType === "content"
          ? "Content Only"
          : "Unknown"
      }})
    </h1>
    <div style="margin-bottom: 10px">
      <div @click="alertTypeLeft" style="display: inline-block">
        <ActionButton
          buttonType="secondary"
          :buttonTheme="
            store.selected === 'blue'
              ? 'red'
              : store.selected === 'red'
              ? 'orange'
              : store.selected === 'orange'
              ? 'green'
              : store.selected === 'green'
              ? 'blue'
              : 'unknown'
          "
          buttonStyle="all"
          :buttonLabel="
            store.selected === 'blue'
              ? 'Error'
              : store.selected === 'red'
              ? 'Warning'
              : store.selected === 'orange'
              ? 'Success'
              : store.selected === 'green'
              ? 'Information'
              : 'Unknown'
          "
          arrow="left"
        />
      </div>
      <div @click="alertTypeRight" style="display: inline-block">
        <ActionButton
          buttonType="secondary"
          :buttonTheme="
            store.selected === 'blue'
              ? 'green'
              : store.selected === 'green'
              ? 'orange'
              : store.selected === 'orange'
              ? 'red'
              : store.selected === 'red'
              ? 'blue'
              : 'unknown'
          "
          buttonStyle="all"
          :buttonLabel="
            store.selected === 'blue'
              ? 'Success'
              : store.selected === 'green'
              ? 'Warning'
              : store.selected === 'orange'
              ? 'Error'
              : store.selected === 'red'
              ? 'Information'
              : 'Unknown'
          "
          arrow="right"
        />
      </div>
    </div>
    <div style="display: flex; justify-content: space-between">
      <div @click="modalTypeLeft">
        <ActionButton
          buttonType="primary"
          :buttonTheme="store.selected"
          buttonStyle="icon"
          arrow="left"
        />
      </div>
      <Modal />
      <div @click="modalTypeRight">
        <ActionButton
          buttonType="primary"
          :buttonTheme="store.selected"
          buttonStyle="icon"
          arrow="right"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.colourContainer {
  display: inline-block;
  width: 50px;
  height: 50px;
  border-radius: 8px;
  margin-left: 10px;
  margin-right: 10px;
  cursor: pointer;
}

.colourContainer:hover {
  transform: scale(1.1);
}

.colourContainer:active {
  border: 3px solid black;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
}
</style>
