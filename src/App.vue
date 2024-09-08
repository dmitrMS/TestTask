<template>
  <div class="landing">
  <Menubar/>
  <CompanyLending/>
  <Features
      heading="Наши преимущества"
      :featuresFirst="[
        { title: 'Высокая скорость', description: 'Молниеносные загрузки страниц.' },
        { title: 'Легкость в использовании', description: 'Простота и удобство работы.' },
        { title: 'Гибкость', description: 'Гибкие возможности настройки.' },
      ]"
      :featuresSecond="[
        { title: 'Высокая скорость', description: 'Молниеносные загрузки страниц.' },
        { title: 'Легкость в использовании', description: 'Простота и удобство работы.' },
        { title: 'Гибкость', description: 'Гибкие возможности настройки.' },
      ]"
    />
</div>
</template>

<script>
import Menubar from './components/Menubar/Menubar.vue';
import CompanyLending from './components/CompanyLanding/CompanyLending.vue';
import Features from './components/Features/Features.vue';

export default {
  name: 'App',
  components: {
    Menubar,
    CompanyLending,
    Features
  }
}
</script>

<style>
body {

  /* overflow: auto; */
  margin: 0;
  font-family: 'Arial', sans-serif;
}

.landing {
  position: relative;
}

/* body::-webkit-scrollbar {
  display: none;
} */

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}
</style>
