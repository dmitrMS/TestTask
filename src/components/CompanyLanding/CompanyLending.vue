<template>
  <div class="main-picture">
    <img src="@/assets/blueTheme.svg" class="main-picture-blue" loading="lazy"/>
    <img src="@/assets/main-theme-town.svg" class="main-picture-town" loading="lazy"/>
    <img src="@/assets/humans.svg" class="main-picture-humans" loading="lazy"/>
    <div class="main-picture-landing">
      <h1 class="main-picture-landing__h2">
        Энергия твоего роста - заряжаем твою карьеру!
      </h1>
      <button @click="openModal" class="main-picture-landing__button">
        Стать частью команды
      </button>
    </div>
  </div>

  <!-- Подключаем компонент модального окна -->
  <JobApplicationModal
    :isOpen="isModalOpen"
    @close="closeModal"
    @submit="submitApplication"
  />
</template>

<script>
import JobApplicationModal from "../ModalModule/Modal.vue";
import "./CompanyLending.scss";

export default {
  name: "CompanyLending",
  data() {
    return {
      isModalOpen: false,
    };
  },
  components: {
    JobApplicationModal,
  },
  methods: {
    openModal() {
      this.isModalOpen = true;
    },
    closeModal() {
      this.isModalOpen = false;
    },
    submitApplication(form) {
      console.log("Данные отправлены:", form);
      this.closeModal();
    },
  },
};
</script>

