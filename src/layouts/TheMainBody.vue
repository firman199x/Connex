<template>
  <div class="main-body-body_wrapper">
    <TheSavedReq />
    <TheReqEditor />
    <TheRespViewer />
    <TheHistory />
  </div>
</template>

<script>
import TheSavedReq from "../components/mainBody/TheSavedReq.vue";
import TheReqEditor from "../components/mainBody/TheReqEditor.vue";
import TheRespViewer from "../components/mainBody/TheRespViewer.vue";
import TheHistory from "../components/mainBody/TheHistory.vue";

export default {
  name: "TheMainBody",
  components: {
    TheSavedReq,
    TheReqEditor,
    TheRespViewer,
    TheHistory,
  },
};
</script>

<style>
.main-body-body_wrapper {
  display: flex;
  justify-content: center;
  background-color: #333;
  color: white;
  text-align: center;
  margin: 0px 5px 5px;
  flex-grow: 1;
}

.main-body-sub-section {
  background-color: #333;
  color: white;
  padding: 0rem 1rem;
  text-align: center;
  border-radius: 5px;
  margin: 5px;
  flex: auto;

  display: flex;
  flex-direction: column;
}

.main-body-button-area {
  height: 3rem;
  background-color: #333333;
  border-radius: 8px;
  margin: 8px 0px;

  display: flex;
}

.main-body-badge-area {
  height: 2.4rem;
  background-color: #333333;
  border-radius: 8px;
  margin: 0px 0px 0px;

  display: flex;
}
</style>
