<template>
  <div id="card" >
    <!-- <header  class="navbar navbar-light">
      <button class="navbar-toggler sidebar-toggler" type="button" data-toggle="sidebar-show">
        <span class="navbar-toggler-icon"></span>
      </button>
    </header> -->
    <center>
      <h1>DASHBOARD</h1>
     <hr>
      <div>
        <b-img :src="require('assets/user.png')" rounded="circle" alt="Circle image" id="userIcon"></b-img>
      </div>
      <h2>Hi {{Uname}}</h2>
      <p>Welcome to the Dashboard</p>
      <b-button v-on:click="redirect('/authorizationForm')" variant="primary">Connect</b-button>
    </center>
  </div>
</template>
<style lang='scss' scoped>
@import "~assets/colors.scss";
#card {
  margin-top: 10%;
}
#userIcon {
  width: $userIconWidth !important;
  height: $userIconHeight !important;
}
</style>

<script>
import ROUTER from "router"
export default {
  name: "card",
  data() {
    return {
      Uname: sessionStorage.getItem("Username")
    };
  },
  component: {

  },
  methods: {
    redirect(route){
      ROUTER.push(route);
    }
  }
};
</script>