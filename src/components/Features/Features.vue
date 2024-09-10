<template>
  <section class="features">
    <div class="container">
      <div class="features-list">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="feature-item"
        >
          <div class="feature-content">
            <img :src="getImagePath(feature.icon)" />
            <h3>{{ feature.title }}</h3>
            <!-- <p>{{ feature.description }}</p> -->
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import "./Features.css";

export default {
  name: "FeaturesSection",
  props: {
    features: Array,
  },
  methods: {
    // Метод для формирования пути к изображению
    getImagePath(imageName) {
      return require(`@/assets/${imageName}`);
    },
  },
};
</script>
