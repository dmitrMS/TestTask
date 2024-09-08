<template>
  <nav class="menubar">
    <div class="logo">
      <img src="@/assets/CADesign.svg" loading="lazy" />
    </div>
    <ul class="menu">
        <li
          v-for="(item, index) in menuItems"
          :key="index"
          @click="selectItem(index)"
          :class="selectedIndex===index ? 'menu__li-active' : 'menu__li'"
        >
          <a href="#" class="menu__li-a">{{ item }}</a>
        </li>
    </ul>
  </nav>
</template>
/* eslint-disable */
<script>
import "./Menubar.css";

export default {
  name: "Menubar",
  data() {
    return {
      // Пункты меню
      menuItems: [
        "О нас",
        "Наши ценности",
        "Вакансии",
        "Начало карьеры",
        "Контакты",
        "Социальные сети",
      ],
      // Индекс выбранного пункта, по нему идёт опредение активности
      selectedIndex: null,
    };
  },
  methods: {
    // Активация элемента
    selectItem(index) {
      this.selectedIndex = index;
    },
  },
};
</script>
