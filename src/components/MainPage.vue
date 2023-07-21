<template>
  <div class="wrapper">
    <div class="center">
      <div class="allCafes">
        <h1 class="title" style="margin-bottom: 20px">Кафе поблизости</h1>
        <template v-if="rawObjectOrArray">
          <OneCafe
            v-for="item in rawObjectOrArray"
            :dataForOneCafe="item"
            :key="item.id"
          />
        </template>
      </div>
      <div class="randomizer">
        <div v-if="rawObjectOrArray">
          <CafeRandomizer :cafes="rawObjectOrArray" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { toRaw } from "vue";
import OneCafe from "./OneCafe.vue";
import CafeRandomizer from "./CafeRandomizer.vue";

export default {
  name: "MainPage",
  components: {
    OneCafe,
    CafeRandomizer,
  },
  data() {
    return {
      data: "",
      rawObjectOrArray: null,
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    async getData() {
      try {
        const response = await axios.get(
          "https://bandaumnikov.ru/api/test/site/get-index"
        );
        this.data = response.data;

        if (this.data) {
          this.rawObjectOrArray = toRaw(this.data).data;
        }
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
.center {
  margin: 20px auto;
  display: flex;
  justify-content: space-around;
  color: black;
}

.randomizer {
  margin-top: 20px;
}

.allCafes {
  margin-top: 20px;
  margin-right: 20px;
}

@media (max-width: 1300px) {
  .center {
    margin: 20px 30px;
  }
}

@media (max-width: 860px) {
  .center {
    flex-direction: column-reverse;
  }
}

@media (max-width: 650px) {
  .center {
    width: 100%;
    margin: 0;
  }

  .allCafes {
    margin-right: 0;
  }

  .title {
    margin-left: 15px;
  }
}
</style>
