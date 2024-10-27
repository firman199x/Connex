<template>
  <div>
    <q-select bg-color="secondary" filled v-model="model" use-input input-debounce="0" @new-value="createValue" label="Server" :options="filterOptions" @filter="filterFn" style="width: 250px" />
    <q-input bg-color="secondary" outlined v-model="ipPort" label="wss:\\ip:port" style="margin-left: 10px" />
    <q-btn square outline color="secondary" icon="save" style="margin-left: 10px; height: 3rem; border-radius:5px;" />
    <q-btn color="lime" outline label="Connected" style="height:3rem;
      width: 15rem; margin-left: 5rem; border-radius:5px;" self-end />
  </div>
</template>

<script>
import { ref } from 'vue'

const stringOptions = [
  'xProjectServer', 'xFileServer', 'xCommServer', 'xProxy', 'xAlarmServer',
  'SafeGeneral', 'SafeAlarm', 'SafeComm', 'SafeFile', 'SafeProject',
]

export default {
  setup() {
    const model = ref('SafeProject')
    const ipPort = ref('localhost:65250')
    const filterOptions = ref(stringOptions)

    return {
      model,
      ipPort,
      filterOptions,

      createValue(val, done) {
        // Calling done(var) when new-value-mode is not set or is "add", or done(var, "add") adds "var" content to the model
        // and it resets the input textbox to empty string
        // ----
        // Calling done(var) when new-value-mode is "add-unique", or done(var, "add-unique") adds "var" content to the model
        // only if is not already set and it resets the input textbox to empty string
        // ----
        // Calling done(var) when new-value-mode is "toggle", or done(var, "toggle") toggles the model with "var" content
        // (adds to model if not already in the model, removes from model if already has it)
        // and it resets the input textbox to empty string
        // ----
        // If "var" content is undefined/null, then it doesn't tampers with the model
        // and only resets the input textbox to empty string

        if (val.length > 0) {
          const modelValue = (model.value || []).slice()

          val
            .split(/[,;|]+/)
            .map(v => v.trim())
            .filter(v => v.length > 0)
            .forEach(v => {
              if (stringOptions.includes(v) === false) {
                stringOptions.push(v)
              }
              if (modelValue.includes(v) === false) {
                modelValue.push(v)
              }
            })

          done(null)
          model.value = modelValue
        }
      },

      filterFn(val, update) {
        update(() => {
          if (val === '') {
            filterOptions.value = stringOptions
          }
          else {
            const needle = val.toLowerCase()
            filterOptions.value = stringOptions.filter(
              v => v.toLowerCase().indexOf(needle) > -1
            )
          }
        })
      }
    }
  }
}
</script>
<style scoped>
div {
  background-color: #333;
  color: white;
  margin: 0px 5px;
  padding: 0.2rem 0 1rem;
  text-align: center;
  height: 65px;

  display: flex;
}
</style>
