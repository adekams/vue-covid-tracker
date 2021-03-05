 <template>
  <div id="app" class="container">
    <Header />
    <Tracker />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tracker from './components/Tracker.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tracker,
    Footer,
  },
}
</script>

<style>
#app {
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
