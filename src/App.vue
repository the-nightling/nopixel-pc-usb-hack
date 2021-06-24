<template>
  <div id="app">
    <SettingsPanel :splashScreenInterval.sync="splashScreenInterval" :displayPasswordInterval.sync="displayPasswordInterval" :inputInterval.sync="inputInterval" />
    <StartScreen v-if="state == 'reset'" @click="start" />
    <SplashScreen v-if="state == 'splash'" />
    <PasswordScreen v-if="state == 'password'" :password="password" @mounted="(p) => password = p" />
    <InputScreen v-if="state == 'input'" :text.sync="userInput" @enter="validate" />
    <ValidateScreen v-if="state == 'validate'" :actualPassword="password" :userInput="userInput" @click="reset" />
  </div>
</template>

<script>
import StartScreen from "./components/StartScreen.vue";
import SplashScreen from "./components/SplashScreen.vue";
import PasswordScreen from "./components/PasswordScreen.vue";
import InputScreen from "./components/InputScreen.vue";
import ValidateScreen from "./components/ValidateScreen.vue";
import SettingsPanel from "./components/SettingsPanel.vue";

export default {
  name: "App",
  components: {
    StartScreen,
    SplashScreen,
    PasswordScreen,
    InputScreen,
    ValidateScreen,
    SettingsPanel
  },
  data() {
    return {
      state: "reset",
      password: '',
      userInput: '',
      splashScreenInterval: 2000,
      displayPasswordInterval: 3000,
      inputInterval: 7000
    };
  },
  methods: {
    start() {
      this.state = 'splash';
      setTimeout(() => {
        this.state = 'password';
        setTimeout(() => {
          this.state = 'input';
          setTimeout(() => {
            if (this.state != 'validate')
              this.state = 'validate';
             }, this.inputInterval);
        }, this.displayPasswordInterval);
      }, this.splashScreenInterval);
    },

    validate() {
      this.state = 'validate';
    },

    reset() {
      this.state = 'reset';
      this.password = '';
      this.userInput = '';
    }
  }
};
</script>

<style>
body {
  background-image: url('./assets/vault-bg.png');
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
}

.terminal {
  background-color:#3d444e;
  position:absolute;
  height: 170px;
  width: 430px;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  color: white;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
