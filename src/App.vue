<template>
  <div class="landing">
  <Menubar/>
  <CompanyLending/>
  <Features
      :features="[
        { title: 'Развитие', description: 'что-то',icon:'Rasvitie.svg' },
        { title: 'Обучение', description: 'что-то',icon:'Obychenie.svg' },
        { title: 'Ответсвенность', description: 'Гибкие возможности настройки.',icon:'Otvetstvennost.svg' },
        { title: 'Динамика', description: 'Общего центра обслуживания.Современные технологии, проекты, рабочие группы',icon:'Dynamic.svg' },
        { title: 'Комфорт', description: 'что-то',icon:'Komfort.svg' },
        { title: 'Надёжность', description: 'что-то',icon:'Nadezhnost.svg' },
      ]"
    />
    <GeneralManager/>
</div>
</template>

<script>
import Menubar from './components/Menubar/Menubar.vue';
import CompanyLending from './components/CompanyLanding/CompanyLending.vue';
import Features from './components/Features/Features.vue';
import GeneralManager from './components/GeneralManagerInfo/GeneralManager.vue';

export default {
  name: 'App',
  components: {
    Menubar,
    CompanyLending,
    Features,
    GeneralManager
  }
}
</script>

<style>
body {

   overflow: auto; 
  margin: 0;
  font-family: 'Arial', sans-serif;
}

.landing {
  position: relative;
}

 body::-webkit-scrollbar {
  display: none;
} 

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}
</style>
