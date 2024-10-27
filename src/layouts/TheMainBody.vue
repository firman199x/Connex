<template>
  <div class="main-body-body_wrapper">
    <TheSavedReq />
    <TheReqEditor />
    <TheRespViewer />
    <TheHistory />
  </div>
</template>

<script>
import TheSavedReq from '../components/mainBody/TheSavedReq.vue'
import TheReqEditor from '../components/mainBody/TheReqEditor.vue'
import TheRespViewer from '../components/mainBody/TheRespViewer.vue'
import TheHistory from '../components/mainBody/TheHistory.vue'

export default {
  name: 'TheMainBody',
  components: {
    TheSavedReq,
    TheReqEditor,
    TheRespViewer,
    TheHistory
  }
};
</script>

<style>

.main-body-body_wrapper {
  display: flex;
  justify-content: center;
  background-color: #333;
  color: white;
  text-align: center;
  margin: 5px;
  border-radius: 5px;
  flex-grow: 1;
}

.main-body-sub-section {
  background-color: #333;
  color: white;
  padding: 1rem;
  text-align: center;
  border-radius: 5px;
  margin: 5px;
  flex: auto;

  display: flex;
  flex-direction: column;
}

.main-body-side {
  max-width: 350px;
  background-color: #282828;
}

.main-body-button-area {
  height: 3rem;
  background-color: #333333;
  border-radius: 8px;
  margin: 8px 0px;

  display: flex;
}

</style>

