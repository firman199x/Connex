<template>
  <div class="q-pa-md q-gutter-sm main-body-sub-section main-body-side"
    style="background-color: #ffffff; overflow: hidden; max-width:350px">
    <q-input ref="filterRef" filled v-model="filter" label="Filter">
      <template v-slot:append>
        <q-icon v-if="filter !== ''" name="clear" class="cursor-pointer" @click="resetFilter" />
      </template>
    </q-input>
    <q-tree :nodes="simple" node-key="label" :filter="filter" dense default-expand-all style="font-size: 0.8rem;" />
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const filter = ref('')
    const filterRef = ref(null)

    return {
      filter,
      filterRef,

      simple: [
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
            { label: 'OpQueryTag' },
            { label: 'OpSetTagNotification' }
          ]
        },
        {
          label: 'XALARMAPI',
          children: [
            { label: 'OpSubAlarm' },
            { label: 'OpNotifyAlarm' }
          ]
        },
        {
          label: 'XRTDBWRAPPER',
          children: [
            { label: 'OpQuery' },
            { label: 'OpUpdate' },
            { label: 'OpSetNotification' },
            { label: 'OpCancelNotification' },
            { label: 'OpDeleteRow' }
          ]
        }
      ],

      resetFilter() {
        filter.value = ''
        filterRef.value.focus()
      }
    }
  }
}
</script>
