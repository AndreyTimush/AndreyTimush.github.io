<template>
  <div class="wrapper">
    <div class="row">
      <img :src="dataForOneCafe.photo || require('../assets/default.png')" />
      <CafeData
        class="data"
        :cafe="dataForOneCafe && dataForOneCafe"
        :key="dataForOneCafe.id"
      />
    </div>
  </div>
</template>

<script>
import CafeData from "./CafeData.vue";

export default {
  name: "OneCafe",
  props: {
    dataForOneCafe: {
      type: Object,
      required: true,
    },
  },
  components: {
    CafeData,
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  text-align: left;
  box-sizing: border-box;
}

p {
  margin-bottom: 10px;
}

.data {
  margin-left: 15px;
  margin-top: 15px;
}

.row {
  display: flex;
  padding: 10px;
  margin-bottom: 10px;
  transition: background-color 0.5s, box-shadow 0.5s;
}

.row:hover {
  background-image: white;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}

img {
  width: 400px;
  height: 400px;
  object-fit: cover;
  object-position: center;
  border-radius: 5px;
}

@media (max-width: 1300px) {
  img {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 650px) {
  .row {
    flex-direction: column;
    padding: 0;
    transition: none;
  }

  .row:hover {
    box-shadow: none;
  }

  img {
    width: 100%;
    border-radius: 0;
  }
}
</style>
