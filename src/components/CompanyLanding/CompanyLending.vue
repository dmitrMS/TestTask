<template>
  <div class="main-picture">
    <img src="@/assets/blueTheme.svg" class="main-picture-blue" />
    <img src="@/assets/main-theme-town.svg" class="main-picture-town" />
    <img src="@/assets/humans.svg" class="main-picture-humans" />
    <div class="main-picture-landing">
      <h1 class="main-picture-landing__h2">
        Энергия твоего роста - заряжаем твою карьеру!
      </h1>
      <button @click="openModal" class="main-picture-landing__button">Стать частью команды</button>
    </div>
  </div>

  <!-- Модальное окно отклика на вакансию -->
  <div v-if="isModalOpen" class="modal-overlay" @click.self="closeModal">
    <div class="modal-content">
      <button class="close-button" @click="closeModal">X</button>
      <h2>Отклик на вакансию</h2>
      <form @submit.prevent="submitApplication">
        <div class="form-group">
          <label for="name">Имя</label>
          <input v-model="form.name" type="text" id="name" required />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input v-model="form.email" type="email" id="email" required />
        </div>
        <div class="form-group">
          <label for="resume">Прикрепить резюме</label>
          <input type="file" id="resume" @change="handleFileUpload" />
        </div>
        <div class="form-group">
          <label for="message">Сообщение</label>
          <textarea v-model="form.message" id="message" rows="4"></textarea>
        </div>
        <button type="submit" class="submit-button">Отправить</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "CompanyLending",
  data() {
    return {
      isModalOpen: false,
      form: {
        name: "",
        email: "",
        resume: null,
        message: ""
      }
    };
  },
  methods: {
    openModal() {
      this.isModalOpen = true;
    },
    closeModal() {
      this.isModalOpen = false;
    },
    handleFileUpload(event) {
      this.form.resume = event.target.files[0];
    },
    submitApplication() {
      console.log("Отправлено:", this.form);
      // Очистка формы
      this.form = {
        name: "",
        email: "",
        resume: null,
        message: ""
      };
      this.closeModal();
    }
  }
};
</script>


