<template>
  <div class="main-body-sub-section">
    <div class="main-body-badge-area">
      <q-btn square color="secondary" icon="save" style="margin: 5px 5px 0px 0px;
        height: 1rem; border-radius:5px; " />
      <q-btn outline color="secondary" label="opCode: OpQueryTagByProp" style="margin: 5px ;
        height: 1rem; border-radius:5px; " />
      <q-btn outline color="secondary" label="uid: 1" style="margin: 5px ;
        height: 1rem; border-radius:5px; " />
      <q-btn outline color="secondary" label="SentTime: 23:13:15.532" style="margin: 5px ;
        height: 1rem; border-radius:5px; " />
    </div>
    <textarea v-model="reqJson" class="my-textarea" wrap="off" spellcheck="false" />
    <div class="main-body-button-area" style="flex-direction: row-reverse;">
      <q-btn color="white" text-color="black" label="Send" style="width: 6rem;
        height: 2.5rem;" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const reqJson = ref(JSON.stringify({
      "version": "1.0",
      "requestObjId": "",
      "opCode": "OpQueryTagByProp",
      "uid": 1,
      "dataProvider": "XTAGLIB",
      "dataSource": "runtime",
      "requests": [
        {
          "group": "[fail] {1} - invalid propValue - No custom prop name 'PosXY'",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propValue": {
            "PosXY": 320
          }
        },
        {
          "group": "[valid] {2} - without propValue or propCondition",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "conditions": "ID == 22"
        },
        {
          "group": "[fail] {3} - propValue and propCondition together",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propCondition": "Name=='PosX' AND ValueInteger==1061",
          "propValue": {
            "eq_description": "HSCB Feeder 1",
            "alarm_page": "RTS-WDNS-TPS-ALM"
          }
        },
        {
          "group": "[valid] {4} - but nothing match the propValue",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propValue": {
            "PosY": 20,
            "AtsId": "2"
          }
        },
        {
          "group": "[valid] {5} - two propValue string + tagCondition",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "conditions": "ID > 1756",
          "propValue": {
            "eq_description": "HSCB Feeder 1",
            "alarm_page": "RTS-WDNS-TPS-ALM"
          }
        },
        {
          "group": "[valid] {6} - propValue integer + string",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propValue": {
            "PosY": 320,
            "AtsId": "102"
          }
        },
        {
          "group": "[valid] {7} - propCondition only",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propCondition": "Name=='PosX' AND ValueInteger==1061"
        },
        {
          "group": "[valid] {8} - propValue integer",
          "tagAttr": "ID, Description, DataType, Value, TagName",
          "propValue": {
            "PosY": 320
          }
        }
      ]
    }, null, 4));

    return {
      reqJson
    }
  }
};
</script>

<style scoped>
.my-textarea {
  flex: auto;
  border-radius: 10px;
  margin: 5px 0px 0px;
  font: italic 1rem small-caps bold;
}

</style>
