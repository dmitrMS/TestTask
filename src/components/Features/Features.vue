<template>
    <section class="features">
      <div class="container">
        <h2>{{ heading }}</h2>
        <div class="features-list">
          <div
            v-for="(feature, index) in featuresFirst"
            :key="index"
            class="feature-item"
          >
            <h3>{{ feature.icon }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
        <div class="features-list">
          <div
            v-for="(feature, index) in featuresSecond"
            :key="index"
            class="feature-item"
          >
            <div class="feature-content">
              <h3>{{ feature.icon }}</h3>
              <p>{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "FeaturesSection",
    props: {
      heading: String,
      featuresFirst: Array,
      featuresSecond: Array,
    },
  };
  </script>
  
  