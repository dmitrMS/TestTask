<template>
  <div class="main-general">
    <button class="main-general__button__left"></button>
    <div class="main-general-text">
      <h1 class="main-general-text__h1">Евдокимова Майа</h1>
      <p class="main-general-text-job">Генеральный директор</p>
      <p class="main-general-text-overview">
        Цель нашей работы обеспечить высочайший сервис нашим клиентам. Дать
        возможность бизнесу сосредоточиться на своих ключевых задачах, передав
        функции управления персоналом, казначейства, финансового учёта и
        отчётности нам.
      </p>
    </div>
    <img src="@/assets/GeneralManager.svg" class="main-general__img" />
    <button class="main-general__button__right"></button>
  </div>
  <div class="min-size-general-text">
      <h1 class="min-size-general-text__h1">Евдокимова Майа</h1>
      <p class="min-size-general-text-job">Генеральный директор</p>
      <p class="min-size-general-text-overview">
        Цель нашей работы обеспечить высочайший сервис нашим клиентам. Дать
        возможность бизнесу сосредоточиться на своих ключевых задачах, передав
        функции управления персоналом, казначейства, финансового учёта и
        отчётности нам.
      </p>
  </div>
</template>

<script>
import "./GeneralManager.css";

export default {
  name: "GeneralManager",
  data() {
    return {};
  },
  methods: {},
};
</script>
