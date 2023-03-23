<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <div class="links">
      <a
        v-for="(link, index) in links"
        :key="index"
        :href="link.url"
        target="_blank"
        class="link-item"
      >
        {{ link.title }}
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Linktree Clone",
      links: [],
    };
  },
  mounted() {
    this.fetchLinks();
  },
  methods: {
    fetchLinks() {
      const storedLinks = localStorage.getItem("linktreeLinks");

      if (storedLinks) {
        this.links = JSON.parse(storedLinks);
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-family: "Arial", sans-serif;
}

h1 {
  margin-bottom: 2rem;
}

.links {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.link-item {
  display: inline-block;
  padding: 0.5rem 1rem;
  background-color: #42b883;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  font-size: 1.1rem;
}

.link-item:hover {
  background-color: #2c9e7f;
}
</style>
