<template>
  <div class="admin-container">
    <h1>Admin Panel</h1>
    <div v-if="loggedIn">
      <form @submit.prevent="updateLinks">
        <div v-for="(link, index) in links" :key="index" class="link-form">
          <input
            v-model="links[index].title"
            type="text"
            placeholder="Title"
          />
          <input
            v-model="links[index].url"
            type="text"
            placeholder="URL"
          />
        </div>
        <button type="submit">Update Links</button>
      </form>
    </div>
    <div v-else>
      <p>Please enter the admin password:</p>
      <input v-model="password" type="password" />
      <button @click="login">Log In</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loggedIn: false,
      password: "",
      links: [
        { title: "", url: "" },
        { title: "", url: "" },
        { title: "", url: "" },
        { title: "", url: "" },
      ],
    };
  },
  methods: {
    login() {
      if (this.password === "admin") {
        this.loggedIn = true;
      } else {
        alert("Incorrect password!");
      }
    },
    updateLinks() {
      localStorage.setItem("linktreeLinks", JSON.stringify(this.links));
      alert("Links updated!");
    },
  },
};
</script>

<style scoped>
.admin-container {
  width: 100%;
  max-width: 500px;
  margin: 2rem auto;
  padding: 2rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  font-family: "Arial", sans-serif;
}

h1 {
  margin-bottom: 1rem;
}

.link-form {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}

input[type="text"],
input[type="password"] {
  padding: 0.5rem;
  font-size: 1rem;
}

button {
  display: inline-block;
  padding: 0.5rem 1rem;
  background-color: #42b883;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  font-size: 1.1rem;
  border: none;
  cursor: pointer
}
</style>