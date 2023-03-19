<script>
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import UsersList from "./components/UsersList.vue";

function data() {
  return {
    name: "",
  };
}

function name(newValue) {
  console.log(newValue);
}

function resetName() {
  this.name = "";
}

export default {
  components: { HelloWorld, TheWelcome, UsersList },
  data,
  watch: { name },
  methods: { resetName },
};
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />
    <div class="wrapper">
      <HelloWorld :msg="'Welcome to my humble app'" />
      <div id="form">
        <input type="text" v-model="name" />
        <button @click="resetName">Reset name</button>
      </div>
      <UsersList :name="name" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  gap: 1em;
}

.wrapper {
  display: flex;
  flex-direction: column;
  gap: 1em;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

header button {
  background-color: rgb(0, 139, 93);
  color: white;
  padding: 0.5em;
  font-size: 1em;
  font-weight: bold;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

header input {
  padding: 0.5em;
  font-size: 1em;
  border: none;
  border-radius: 5px;
  width: 100%;
}

#form {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 1em;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
