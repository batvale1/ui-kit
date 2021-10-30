<template>
  <div id="app">
    <MySeparator space="50" />
    <MyContainer gap="8" align="center" :filling="color">
      <MyImage alt="Vue logo" src="https://picsum.photos/200/300" label="new" />
    </MyContainer>
    <MyTitle text="Выберите цвет заливки" component="h2" align="center" />
    <MySeparator space="8" />
    <MyContainer gap="8" column="3">
      <MyInput type="color" id="1" @input="inputHandler" v-model="color" />
      <MyButton text="Скопировать цвет" :disabled="!color" @click="clickHandler" />
      <MyButton text="Сбросить" type="reset" :disabled="!value" @click="resetHandler" />
    </MyContainer>
  </div>
</template>

<script>
import MyTitle from "./components/Title.vue";
import MyImage from "./components/Image.vue";
import MyInput from "./components/Input.vue";
import MyButton from "./components/Button.vue";
import MySeparator from "./components/Separator.vue";
import MyContainer from "./components/Container.vue";

export default {
  name: "App",
  components: {
    MyTitle,
    MyImage,
    MyInput,
    MyButton,
    MySeparator,
    MyContainer
  },
  data() {
    return {
      value: "",
      color: ""
    };
  },
  methods: {
    inputHandler(value) {
      this.color = value;
    },
    clickHandler() {
      this.value = this.color;
      navigator.clipboard.writeText(this.value);
    },
    resetHandler() {
      this.value = "";
      this.color = "";
    }
  }
};
</script>

<style>
#app {
  font-family: var(--font-family);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--black);
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  max-width: 960px;
  margin: 0 auto;
}
</style>
