<template>
  <div v-if="isOpen" class="modal-overlay" @click.self="closeModal">
    <div class="modal-content">
      <button class="close-button" @click="closeModal">X</button>
      <h2 class="modal__h2">Отклик на вакансию</h2>
      <form @submit.prevent="submitApplication" class="form-container">
        <div class="form-group">
          <InputC
            v-model="form.vacancy"
            parameter="Желаемая вакансия"
            type="text"
            required
          />
        </div>

        <div class="form-group">
          <InputC
            v-model="form.fullName"
            parameter="Фамилия, имя и отчество"
            type="text"
            required
          />
        </div>

        <!-- Поля телефона и email в одной строке -->
        <div class="form-group-row">
          <div class="form-group-item">
            <InputC
              v-model="form.phone"
              parameter="Мобильный телефон"
              type="tel"
              required
            />
          </div>

          <div class="form-group-item">
            <InputC
              v-model="form.email"
              parameter="E-mail"
              type="email"
              required
            />
          </div>
        </div>

        <div class="form-group">
          <InputC
            v-model="form.education"
            parameter="Образование"
            type="text"
            required
          />
        </div>

        <div class="form-group">
          <InputC
            v-model="form.address"
            parameter="Адрес места жительства"
            type="text"
            required
          />
        </div>

        <div class="form-group-row">
          <div class="form-group-birthday">
            <InputC
              v-model="form.birthDate"
              parameter="Дата рождения"
              type="date"
              required
            />
          </div>

          <div class="form-group">
            <label for="resume" class="form-group__label">
              Загрузить резюме
            </label>
            <input
              type="file"
              class="form-group-load"
              id="resume"
              @change="handleFileUpload"
            />
          </div>
        </div>

        <div class="form-group-coment">
          <InputC
            v-model="form.comment"
            parameter="Комментарий"
            rows="4"
          ></InputC>
        </div>

        <div class="work-form">
          <input class="work-form__input" type="checkbox" required />
          <p class="work-form__p">Я принимаю условия</p>
          <a href="#" class="work-form__a">передачи информации</a>

          <button type="submit" class="submit-button">Отправить</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import "./Modal.scss";
import InputC from "../../ui/Input/Input.vue";

export default {
  name: "JobApplicationModal",
  props: {
    isOpen: {
      type: Boolean,
      required: true,
    },
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
    InputC,
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