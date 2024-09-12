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

        <!-- Поля телефона и email в одной строке -->
        <div class="form-group-row">
          <div class="form-group-item">
            <Input
              v-model="form.phone"
              parameter="Мобильный телефон"
              type="tel"
              required
            />
          </div>

          <div class="form-group-item">
            <Input
              v-model="form.email"
              parameter="E-mail"
              type="email"
              required
            />
          </div>
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

        <div class="form-group-row">
          <div class="form-group-birthday">
            <Input
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
          <Input
            v-model="form.comment"
            parameter="Комментарий"
            rows="4"
          ></Input>
        </div>

        <div class="work-form">
          <input class="work-form-input" type="checkbox" required />
          <p class="work-form__p">Я принимаю условия</p>
          <a href="#" class="work-form__a">передачи информации</a>

          <button type="submit" class="submit-button">Отправить</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import "./Modal.css";
import Input from "../../ui/Input/Input.vue";

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

<style>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  max-width: 1145px;
  max-height: 1205px;
  margin-left: 15%;
  margin-right: 15%;
  position: relative;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
}

.form-container {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 15px;
  max-width: 712px;
  margin-right: 15px;
  display: flex;
}

.form-group-row {
  display: flex;
}

.form-group-item {
  flex-basis: 48%; /* Поля будут занимать по 48% ширины для равномерного размещения */
  display: flex;
  padding-right: 5px;
  margin-right: 5px;
  flex-direction: column;
}

.form-group-birthday {
  margin-bottom: 15px;
  max-width: 266px;
}

.form-group-coment {
  margin-bottom: 15px;
  max-width: 712px;
  height: 153px !important;
}

.form-group__label {
  margin-top: 5px;
  margin-left: 30px;
  text-decoration: none;
  color: #187cd3;
  cursor: pointer;
}

.form-group input[type="file"] {
  border: none;
  display: none;
}

.work-form__input[type="checkbox"] {
  margin-right: 10px;
}

.work-form__p {
  margin: 0;
}

.work-form__a {
  margin-left: 5px;
  color: #187cd3;
  text-decoration: none;
}

.submit-button {
  background-color: #e9862a;
  color: white;
  font-size: 16px;
  padding: 10px;
  border: none;
  cursor: pointer;
  margin-top: 15px;
  align-self: flex-end;
}

.submit-button:hover {
  background-color: #d7741f;
}

.work-form {
  position: relative;
  width: 712px;
  display: flex;
  align-items: center;
  margin-top: 15px;
  border: 1px grey solid;
}

@media (max-width: 768px) {
  .form-group {
    max-width: 688px;
  }

  .form-group-row {
    flex-direction: column;
  }

  .form-group-item {
    flex-basis: 100%;
  }
}

@media (max-width: 320px) {
  .form-group {
    max-width: 280px;
  }
}
</style>
