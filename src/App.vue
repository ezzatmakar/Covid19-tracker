<template>
  <Header />
  <div class="container content">
    <router-view />
  </div>
  <Footer />
</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'

export default {
  components: {
    Header,
    Footer
  }
}
</script>

<style scoped>
html, body {
  height: 100%;
  margin: 0;
}
body {
  display: flex;
  flex-direction: column;
}
.content {
  min-height: 100%;
}
</style>