
  <template>
  <NavBar/>
  <main class="container-fluid">
    <LoadingSpinner v-if="isLoading" />
    <router-view/>
  </main>
  <Footer/>
</template>

<script>
import NavBar from './components/Navbar.vue';
import Footer from './components/Footer.vue';
export default {
  components: {
    NavBar,
    Footer,
  },

  data() {
    return {
      isLoading: false,
    };
  },
};
</script>
<style src="@/assets/css/style.css"></style>

