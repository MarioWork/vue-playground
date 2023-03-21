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
      <Form @reset-name="resetName" @update-name="updateName" :name="name" />
      <UsersList :name="name" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import UsersList from "./components/UsersList.vue";
import Form from "./components/Form.vue";

function data() {
  return {
    name: "",
  };
}

function name(newValue) {
  console.log(newValue);
}

function updateName(name) {
  this.name = name;
}

function resetName() {
  this.name = "";
}

export default {
  components: { HelloWorld, TheWelcome, UsersList, Form },
  data,
  watch: { name },
  methods: {
    resetName,
    updateName,
  },
};
</script>

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
