<template>
    <div v-if="isOpen" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <button class="close-button" @click="closeModal">X</button>
        <h2 class="modal__h2">Отклик на вакансию</h2>
        <form @submit.prevent="submitApplication" class="form-container">
          <div class="form-group">
            <Input
              v-model="form.vacancy"
              parameter="Желаемая вакансия"
              type="text"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.fullName"
              parameter="Фамилия, имя и отчество"
              type="text"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.phone"
              parameter="Мобильный телефон"
              type="tel"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.email"
              parameter="E-mail"
              type="email"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.education"
              parameter="Образование"
              type="text"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.address"
              parameter="Адрес места жительства"
              type="text"
              required
            />
          </div>
  
          <div class="form-group">
            <Input
              v-model="form.birthDate"
              parameter="Дата рождения"
              type="date"
              required
            />
          </div>
  
          <div class="form-group">
            <textarea
              v-model="form.comment"
              placeholder="Комментарий"
              rows="4"
            ></textarea>
          </div>
  
          <div class="form-group">
            <label for="resume" class="form-group__label">Загрузить резюме</label>
            <input
              type="file"
              class="form-group-load"
              id="resume"
              @change="handleFileUpload"
            />
          </div>
  
          <div class="work-form">
            <input type="checkbox" required />
            <p class="work-form__p">Я принимаю условия</p>
            <a href="#" class="work-form__a">передачи информации</a>
          </div>
  
          <button type="submit" class="submit-button">Отправить</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  import Input from "../../ui/Input/Input.vue";
  
  export default {
    name: "JobApplicationModal",
    props: {
      isOpen: {
        type: Boolean,
        required: true
      }
    },
    data() {
      return {
        form: {
          vacancy: "",
          fullName: "",
          phone: "",
          email: "",
          education: "",
          address: "",
          birthDate: "",
          comment: "",
          resume: null,
        },
      };
    },
    components: {
      Input,
    },
    methods: {
      closeModal() {
        this.$emit("close");
      },
      handleFileUpload(event) {
        this.form.resume = event.target.files[0];
      },
      submitApplication() {
        console.log("Отправлено:", this.form);
        this.$emit("submit", this.form);
        this.form = {
          vacancy: "",
          fullName: "",
          phone: "",
          email: "",
          education: "",
          address: "",
          birthDate: "",
          comment: "",
          resume: null,
        };
        this.closeModal();
      },
    },
  };
  </script>