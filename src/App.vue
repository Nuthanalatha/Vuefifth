<!-- Vue.js Dynamic Components allows the users to switch over the components 
without updating the route of the Vue.js application itself.It also keeps the
data in its current state. It is useful when the user is in a tabbed interface. -->
<!--:is: This field accepts a name string for the registered component or an actual component.-->
<!-- Syntax: In the component section, add the :is field and provide either the variable name or
the component name as follows: <component :is="currentComponent" />-->

<template>
  <navbar-comp />
  <button @click="setSelectedComp('home-comp')">HOME 🏡</button>
  <button @click="setSelectedComp('login-comp')">Login 👉</button>

  <!-- <home-comp v-if="selectedComponent === 'home-comp'" />
  <login-comp v-if="selectedComponent === 'login-cop'" /> -->
  <!-- instead of this two line we can do half line code  -->
  <keep-alive>
    <component :is="selectedComponent"></component>
  </keep-alive>
</template>

<script>
import HomeComp from "./components/HomeComp.vue";
import LoginComp from "./components/LoginComp.vue";
import NavbarComp from "./components/NavbarComp.vue";

export default {
  name: "App",
  components: {
    NavbarComp,
    HomeComp,
    LoginComp,
  },
  data() {
    return {
      selectedComponent: "home-comp",
    };
  },
  methods: {
    setSelectedComp(comp) {
      console.log("comp", comp);
      this.selectedComponent = comp;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
