<template>
  <!--eslint-disable-->
  <div>
    <div v-if="signedIn">
      <div id="app">
        <router-view/>
      </div>
    </div>
    <div v-else>
      <button @click="login" class="btn btn-primary">Sign in</button>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import Mgr from "./services/SecurityService";

export default {
  name: "App",
  data() {
    return {
      mgr: new Mgr(),
      signedIn: false
    };
  },
  methods: {
    login: function() {
      this.mgr.signIn();
    }
  },
  mounted() {
    this.mgr.isSignedIn().then(
      signIn => {
        this.signedIn = signIn;
      },
      err => {
        console.log(err);
      }
    );
  }
};
</script>
