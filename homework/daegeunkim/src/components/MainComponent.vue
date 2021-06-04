<template>
  <div class="w-full max-w-xs mx-auto pt-32">
    <LoginComponent/>
    <FooterComponent/>
  </div>
</template>

<script>
import LoginComponent from './LoginComponent.vue'
import FooterComponent from './FooterComponent.vue'

export default {
  name: 'MainComponent',
  components: {
    LoginComponent,
    FooterComponent
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
