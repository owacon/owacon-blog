<template lnag="pug">
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        こんにちは
      </h1>
      <h2 class="subtitle">
        Nuxt.js project
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">Documentation</a>
        <a href="https://github.com/nuxt/nuxt.js" target="_blank" class="button--grey">GitHub</a>
      </div>
    </div>
    <b-collapse :open="false">
      <button class="button is-primary" slot="trigger">Click me!</button>
      <div class="notification">
        <div class="content">
          <h3>
            Subtitle
          </h3>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. <br/> Nulla accumsan, metus ultrices eleifend gravida, nulla nunc varius lectus, nec rutrum justo nibh eu lectus. <br/> Ut vulputate semper dui. Fusce erat odio, sollicitudin vel erat
            vel, interdum mattis neque.
          </p>
        </div>
      </div>
    </b-collapse>
  </section>
</template>

<style lang="scss" scopde>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  /* 1 */
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

<script>
import AppLogo from "~/components/AppLogo.vue";

export default {
  components: {
    AppLogo
  },
  data() {
    return {
      content: {
        text: null
      }
    };
  },
  methods: {
    getFirebaseData() {
      console.log("firebase");
      firebase
        .database()
        .ref("flamelink")
        .on("value", snapshot => {
          if (snapshot.exists()) {
            this.$set(this.content, "text", snapshot.val());
          }
        });
    },
    getFlamelinkData() {
      app.content
        .get("demoid", {fields:['title']})
        .then(products => this.$set(this.content, "text", products))
        .catch(error => console.log("error"));
    }
  },
  mounted: function() {
    this.getFlamelinkData();
  }
};
</script>
