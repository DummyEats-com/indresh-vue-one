<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld :msg="mesg" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import http from "../http-common";
export default {
  name: "home",
  data() {
    return { mesg:{} };
  },
  components: {
    HelloWorld
  },
  mounted() {
    this.getMessage();
  },
  methods: {
    getMessage() {
      http
        .get(`/teams`+`/india-One`)
        .then(response => {
          this.mesg = response.data;
          console.log(response.data);
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>
