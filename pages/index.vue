<template>
  <div class="container">
    <div>
      <Logo />
      <h2 class="title">
        {{ title }}
      </h2>
    </div>
  </div>
</template>
<script>
const axios = require("axios");
const isbn = "978-4-7741-8967-3";
const url = "https://api.openbd.jp/v1/get?isbn=" + isbn;
export default {
  asyncData({ params, error }) {
    return axios
      .get(url)
      .then((res) => {
        return { title: res.data[0].summary.title };
      })
      .catch((e) => {
        error({ title: e.response.status, message: "ERROR!!" });
      });
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
