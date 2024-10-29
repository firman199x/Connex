<template>
  <div class="main-body-sub-section">
    <div class="main-body-badge-area">
      <q-btn
        square
        color="secondary"
        icon="save"
        style="margin: 5px 5px 0px 0px; height: 1rem; border-radius: 5px"
      />
      <q-btn
        outline
        color="secondary"
        label="uid: 1"
        style="margin: 5px; height: 1rem; border-radius: 5px"
      />
      <q-btn
        outline
        color="secondary"
        label="50MB"
        style="margin: 5px; height: 1rem; border-radius: 5px"
      />
      <q-btn
        outline
        color="secondary"
        label="2 sec 12 ms 60 us"
        style="margin: 5px; height: 1rem; border-radius: 5px"
      />
      <q-btn
        outline
        color="secondary"
        label="1/6"
        style="margin: 5px; height: 1rem; border-radius: 5px"
      />
      <q-btn
        outline
        color="secondary"
        label="ReceivedTime: 23:13:15.532"
        style="margin: 5px; height: 1rem; border-radius: 5px"
      />
    </div>
    <textarea
      v-model="respJson"
      class="my-textarea"
      readonly
      wrap="off"
      spellcheck="false"
    />
    <div
      class="main-body-button-area"
      style="flex-direction: row-reverse"
    ></div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const respJson = ref(
      JSON.stringify(
        {
          version: "1.0",
          requestObjId: "",
          opCode: "OpQueryTagByProp",
          uid: 1,
          dataProvider: "XTAGLIB",
          dataSource: "runtime",
          requests: [
            {
              group:
                "[fail] {1} - invalid propValue - No custom prop name 'PosXY'",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propValue: {
                PosXY: 320,
              },
            },
            {
              group: "[valid] {2} - without propValue or propCondition",
              tagAttr: "ID, Description, DataType, Value, TagName",
              conditions: "ID == 22",
            },
            {
              group: "[fail] {3} - propValue and propCondition together",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propCondition: "Name=='PosX' AND ValueInteger==1061",
              propValue: {
                eq_description: "HSCB Feeder 1",
                alarm_page: "RTS-WDNS-TPS-ALM",
              },
            },
            {
              group: "[valid] {4} - but nothing match the propValue",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propValue: {
                PosY: 20,
                AtsId: "2",
              },
            },
            {
              group: "[valid] {5} - two propValue string + tagCondition",
              tagAttr: "ID, Description, DataType, Value, TagName",
              conditions: "ID > 1756",
              propValue: {
                eq_description: "HSCB Feeder 1",
                alarm_page: "RTS-WDNS-TPS-ALM",
              },
            },
            {
              group: "[valid] {6} - propValue integer + string",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propValue: {
                PosY: 320,
                AtsId: "102",
              },
            },
            {
              group: "[valid] {7} - propCondition only",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propCondition: "Name=='PosX' AND ValueInteger==1061",
            },
            {
              group: "[valid] {8} - propValue integer",
              tagAttr: "ID, Description, DataType, Value, TagName",
              propValue: {
                PosY: 320,
              },
            },
          ],
        },
        null,
        4
      )
    );

    return {
      respJson,
    };
  },
};
</script>

<style scoped>
html {
  font-family: sans-serif;
}

.my-textarea {
  flex: auto;
  margin: 5px 0px 0px;
  border-radius: 10px;
  font: italic 1rem small-caps bold;
}
</style>
