<template>
  <div class="body-background">
    <div class="container">
      <div id="view">
        <div id="view1">My</div>
        <div id="view2">Resume</div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h4 class="display-4 text-center text-white">Skills</h4>
          <div
            class="card-container d-flex flex-wrap justify-content-center gap-4"
          >
            <div
              class="card mb-3"
              style="width: 18rem"
              v-for="any in skills"
              :key="any.id"
            >
              <div class="card">
                <div class="card-inner">
                  <div class="card-front">
                    <img :src="any.title" class="card-text w-50" />
                  </div>
                  <div class="card-back">
                    <p class="card-text text-sm">{{ any.experience }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <a
        class="btn btn-dark"
        target="_blank"
        href="https://docs.google.com/document/d/1Xttm3K48mRTXG54W3rzKmEe9kgQebRTW-m_kF_eirCk/edit?usp=sharing"
        role="button"
        >Resume</a
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'ResumeView',
  computed: {
    education() {
      return this.$store.state.education;
    },
    skills() {
      return this.$store.state.skills;
    },
  },
  mounted() {
    this.$store.dispatch('fetchData');
  },
};
</script>

<style scoped>
.card {
  width: 300px;
  height: 400px;
  background-color: rgba(71, 69, 71, 0.5);
  border-radius: 10px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  position: relative;
  transition: all 0.3s ease;
}
.card {
  width: 300px;
  height: 200px;
  perspective: 1000px;
}
.card-inner {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.999s;
}
.card:hover .card-inner {
  transform: rotateY(180deg);
}
.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}
.card-front {
  background-color: rgba(71, 69, 71, 0.5);
  color: #fff;
  display: flex;
  align-items: center;
  border-radius: 10px;
  justify-content: center;
  font-size: 24px;
  transform: rotateY(0deg);
}
.card-back {
  background-color: rgba(71, 69, 71, 0.5);
  color: #fff;
  display: flex;
  align-items: center;
  border-radius: 10px;
  justify-content: center;
  font-size: 24px;
  transform: rotateY(180deg);
}
@media (max-width: 576px) {
  p.text-sm {
    font-size: 14px;
  }
}
.card-text {
  margin: 2rem;
}
.text-sm {
  font-size: 0.875rem;
}
</style>
