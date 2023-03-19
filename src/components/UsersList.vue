<template>
  <article>
    <div v-for="{ id, first_name, last_name } in filteredUsers" :key="id">
      {{ `${id}. ${first_name} ${last_name}` }}
    </div>
  </article>
</template>

<script>
async function getUsers() {
  const response = await fetch("https://reqres.in/api/users?page=1");
  const { data } = await response.json();
  return data;
}

export default {
  props: {
    name: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      users: [],
      filteredUsers: [],
    };
  },
  async created() {
    const users = await getUsers();
    this.users = users;
    this.filteredUsers = users;
  },
  watch: {
    name(newValue) {
      this.filteredUsers = newValue
        ? this.users.filter(({ first_name, last_name }) =>
            first_name.includes(newValue || last_name.includes(newValue))
          )
        : this.users;
    },
  },
};
</script>

<style scoped>
article {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.5em;
}

div {
  width: 100%;
  background-color: white;
  color: black;
  padding: 0.2em 1em;
  border-radius: 5px;
}
</style>
