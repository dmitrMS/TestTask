<template>
  <nav class="menubar">
    <div class="logo">
      <img src="@/assets/CADesign.svg" />
    </div>
    <ul class="menu">
      <div class="menu__li">
      <li
        v-for="(item, index) in menuItems"
        :key="index"
        @click="selectItem(index)"
        :class="{ active: selectedIndex === index }"
      >
        <a href="#" class="menu__li-a">{{ item }}</a>
      </li>
    </div>
    </ul>
  </nav>
</template>

<script>
import './Menubar.css';

export default {
  name: "Menubar",
  data() {
    return {
      // Пункты меню
      menuItems: ["О нас", "Наши ценности", "Вакансии", "Начало карьеры", "Контакты", "Социальные сети"],
      // Индекс выбранного пункта, по нему идёт опредение активности
      selectedIndex: 0,
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

