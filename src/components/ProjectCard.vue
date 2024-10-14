<template>
  <div class="project-card">
    <h3>{{ title }}</h3>
    <p>{{ description }}</p>
    <a :href="link" target="_blank">View on {{ platform }}</a>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    description: String,
    link: String,
    platform: {
      type: String,
      default: 'GitHub',
    },
  },
}
</script>

<style scoped>
.project-card {
  background: var(--background-blur);
  backdrop-filter: blur(10px);
  padding: 20px;
  border-radius: 10px;
  border: 1px solid rgba(200, 200, 200, 0.8);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.project-card h3 {
  margin: 0;
  font-size: 1.5em;
}

.project-card p {
  font-size: 1em;
  color: #eee;
}

.project-card a {
  color: #007acc;
  text-decoration: none;
}

.project-card a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}
</style>
