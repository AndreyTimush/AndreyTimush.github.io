<template>
  <div class="wrapper">
    <div class="textAndButton">
      <h1>Пообедаем?</h1>
      <h4 class="pressButtonText">
        Нажми на кнопку и мы подберем кафе автоматически
      </h4>
      <div class="button" @click="buttonClicked"><p>Выбрать кафе</p></div>
    </div>
    <div class="imgAndData">
      <img
        :src="
          (randomObject && randomObject.photo) ||
          require('../assets/default.png')
        "
      />
      <CafeData class="data" :cafe="randomObject" v-if="randomObject" />
    </div>
  </div>
</template>

<script>
import CafeData from "./CafeData.vue";

export default {
  name: "CafeRandomizer",
  props: {
    cafes: {
      type: Object,
      required: true,
    },
  },
  components: {
    CafeData,
  },
  data() {
    return {
      randomObject: null,
    };
  },
  methods: {
    buttonClicked() {
      if (this.cafes) {
        this.randomObject =
          this.cafes[Math.floor(Math.random() * this.cafes.length)];
      }
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: black;
}

.textAndButton {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.pressButtonText {
  margin: 10px 0;
}

.button {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2px 7px;
  height: 40px;
  background-color: #605858;
  color: white;
  margin-bottom: 20px;
  width: fit-content;
}

.button:hover {
  cursor: pointer;
  background-color: #726969;
}

.button:active {
  background-color: #534949;
}

img {
  width: 400px;
  height: 400px;
  object-fit: cover;
  object-position: center;
  border-radius: 5px;
}

.data {
  margin-top: 10px;
}

@media (max-width: 1300px) {
  img {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 650px) {
  img {
    width: 100%;
    border-radius: 0;
  }

  .data {
    margin-left: 15px;
  }

  .imgAndData {
    position: realtive;
    width: 100%;
  }
}
</style>
