<template>
<div class="container">
  <div id="app">
    <AndHeader :banner="header_banner" :sub_banner="sub_header_banner">
    </AndHeader>
    <AndContent :optional="digit" :app_title="app.name" :app_version="app.version">
    </AndContent>
    <AndFooter @transfer="logMe" :banner="footer_banner" :link="footer_link">
    </AndFooter>
  </div>
</div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import Content from "./components/Content";
import moment from "moment";
import "../node_modules/bootstrap/scss/bootstrap.scss";

export default {
  data() {
    return {
      app: {
        name: "AndCalculator",
        version: "v1",
        year: moment().format("YYYY")
      },
      header_banner: "Welcome to Andriawan Mini Calculator",
      sub_header_banner: "First Open Project in Vue",
      footer_banner: "Andriawan",
      footer_link: "https://irwan.andriawan.com",
      digit : 0
    };
  },
  // Component dapat ditulis singkat
  // tanpa key object, namun jika ada key
  // maka key akan menjadi tagnya
  components: {
    AndHeader: Header,
    AndFooter: Footer,
    AndContent: Content
  },
  methods: {
    setHeaderBanner(data) {
      this.header_banner = data;
    },
    logMe(e) {
      console.log(e);
    }
  },
  // dipanggil saat pertama kali view dirender
  mounted() {
    if (!this.header_banner) {
      this.setHeaderBanner("test");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
</style>
