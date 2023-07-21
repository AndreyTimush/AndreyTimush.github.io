<template>
  <div class="data">
    <p>Название: {{ cafe && cafe.name }}</p>
    <p>Адрес: {{ (cafe && cafe.address) || "Данные отсутствуют" }}</p>
    <p>Ориентир: {{ (cafe && cafe.landmark) || "Данные отсутствуют" }}</p>
    <p>
      Расстояние:
      {{ (cafe && cafe.distance + " м") || "Данные отсутствуют" }}
    </p>
    <p>Время: {{ (cafe && cafe.time + " мин.") || "Данные отсутствуют" }}</p>
    <p>Кухня: {{ (cafe && cafe.cuisine) || "Данные отсутствуют" }}</p>
    <p>Бизнес-ланч: {{ cafe && cafe.business_lunch ? "Есть" : "Нет" }}</p>
    <p>Цена: {{ (cafe && cafe.price + " Р") || "Данные отствуют" }}</p>
  </div>
</template>

<script>
export default {
  name: "CafeData",
  props: {
    cafe: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style>
.data {
  text-align: left;
  margin-top: 10px;
}

p {
  margin-bottom: 10px;
}
</style>
