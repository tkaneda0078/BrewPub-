<template>
  <section class="section">{{ shop }}</section>
</template>

<script>
export default {
  data() {
    return {
      shop: []
    };
  },
  validate({ params }) {
    return /^\d+$/.test(params.id);
  },
  async asyncData({ app, error, params }) {
    const apiUrl = `http://127.0.0.1:8088/api/v1/shop/${params.id}`;
    return await app.$axios
      .$get(apiUrl)
      .then(res => {
        return { shop: res };
      })
      .catch(e => {
        error({ statusCode: 404, message: "ページが見つかりません" });
      });
  }
};
</script>
