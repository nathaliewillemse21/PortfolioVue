<template>
  <div class="body-background">
    <div class="container">
      <div id="view">
        <div id="view1">My</div>
        <div id="view2">Projects</div>
      </div>
      <div class="card" v-for="info in projects" :key="info.id">
        <img :src="info.image" class="card-img-top" alt="Project Image" />
        <div class="card-body">
          <h5 class="card-title">{{ info.name }}</h5>
          <p class="card-text">{{ info.description }}</p>
          <a :href="info.gitHub" class="btn btn-primary" target="_blank"
            >GitHub</a
          >
          <a :href="info.vercel" class="btn btn-secondary" target="_blank"
            >Vercel</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProjectView',
  computed: {
    projects() {
      return this.$store.state.projects;
    },
  },
  mounted() {
    this.$store.dispatch('fetchData');
  },
};
</script>

<style scoped>
.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.card {
  flex: 0 1 calc(30% - 20px);
  margin: 10px;
  box-sizing: border-box;
  background-color: rgba(71, 69, 71, 0.5);
}

.card-img-top {
  max-width: 100%;
  min-height: auto;
}
.card-title {
  font-style: italic;
  color: antiquewhite;
}
.card-text {
  font-style: italic;
  color: antiquewhite;
}
.card-body {
  text-align: center; /* Optional: Center the text within the card body */
}

.btn {
  margin-top: 10px; /* Optional: Adjust the spacing between the buttons and text */
}

@media (max-width: 768px) {
  .card {
    flex: 0 1 calc(45% - 20px);
  }
}

@media (max-width: 576px) {
  .card {
    flex: 0 1 calc(100% - 20px);
  }
}
</style>
