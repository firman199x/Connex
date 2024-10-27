<template>
  <div class="main-body-sub-section">

    <div class="main-body-badge-area">
      <q-btn square color="secondary" icon="save" style="margin: 5px 0px 0px;
        height: 1rem; border-radius:5px; " />
      <slot id="badges"> </slot>
    </div>

    <textarea class="my-textarea" wrap="off" />

    <div class="main-body-button-area" style="flex-direction: row-reverse;">
      <slot id="bottomButtons"></slot>
      <!-- <q-btn color="white" text-color="black" label="Send" style="width: 6rem; -->
      <!--   height: 2.5rem;" /> -->
    </div>

  </div>
</template>

<style scoped>
.my-textarea {
  flex: auto;
  border-radius: 10px;
  font: italic 1rem small-caps bold;
}
</style>

