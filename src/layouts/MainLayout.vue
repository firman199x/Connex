<template>
  <div class="wrapper">
    <TheHeader />
    <TheMainBody />
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import TheHeader from './TheHeader.vue'
import TheMainBody from './TheMainBody.vue'

export default defineComponent({
  name: 'MainLayout',
  components: {
    TheHeader,
    TheMainBody
  }
})
</script>

<style>
html, body, #q-app {
  height: 100%;
  font: italic 1rem small-caps bold;
  background-color: #333333;
}

.wrapper {
  display: flex;
  flex-direction: column;
  margin: 5px 5px;
  height: 100%;
}
</style>

