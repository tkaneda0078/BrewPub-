<template>
  <section class="section">
    <div class="columns is-mobile">
      <div class="card" v-for="shop in shops" :key="shop.id">
        <div class="card-image">
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image" />
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <p class="title is-4">{{ shop.name }}</p>
            </div>
          </div>
          <div class="content">
            <p>{{ shop.address }}</p>
            <a href="tel">{{ shop.tel }}</a>
          </div>
          <div class="buttons">
            <b-button type="is-primary" expanded>detail</b-button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      shops: []
    };
  },
  async asyncData({ app }) {
    const apiUrl = "http://127.0.0.1:8088/api/v1/shops";
    const res = await app.$axios.$get(apiUrl);
    return {
      shops: res
    };
  }
};
</script>
