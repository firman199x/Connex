<template>
  <div class="q-pa-md q-gutter-sm main-body-sub-section main-body-side"
    style="background-color: #b6b6b6; overflow: hidden;">
    <q-input ref="filterRef" filled v-model="filter" label="Filter">
      <template v-slot:append>
        <q-icon v-if="filter !== ''" name="clear" class="cursor-pointer" @click="resetFilter" />
      </template>
    </q-input>

    <q-tree
      :nodes="simple"
      node-key="label"
      :filter="filter"
      dense
      default-expand-all
    />
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const filter = ref('')
    const filterRef = ref(null)

    return {
      filter,
      filterRef,

      simple: [
        {
          label: 'WebSocket Requests',
          children: [
            {
              label: 'XTAGLIB',
              children: [
                { label: 'OpQueryTag' },
                { label: 'OpSetTagNotification' }
              ]
            },
            {
              label: 'TAGSAFE',
              disabled: false,
              children: [
                { label: 'OpSafeQueryTag' },
                { label: 'OpSafeSetTagNotification' }
              ]
            },
            {
              label: 'RTDBWRAPPER',
              children: [
                { label: 'OpSubAlarm' },
                { label: 'OpNotifyAlarm' }
              ]
            }
          ]
        }
      ],

      resetFilter () {
        filter.value = ''
        filterRef.value.focus()
      }
    }
  }
}
</script>

