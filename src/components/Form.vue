<template>
  <div id="form">
    <input type="text" :value="name" @input="updateName" />
    <button @click="resetName">Reset name</button>
  </div>
</template>

<script>
function resetName() {
  this.$emit("resetName");
}

function updateName(e) {
  this.$emit("updateName", e.target.value);
}

export default {
  emits: ["resetName", "updateName"],
  props: {
    name: {
      type: String,
      default: "",
    },
  },
  methods: { resetName, updateName },
  mounted() {
    console.log(this.name);
  },
};
</script>

<style scoped>
#form {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 1em;
}

input {
  padding: 0.5em;
  font-size: 1em;
  border: none;
  border-radius: 5px;
}

button {
  background-color: rgb(0, 139, 93);
  color: white;
  padding: 0.5em;
  font-size: 1em;
  font-weight: bold;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>
