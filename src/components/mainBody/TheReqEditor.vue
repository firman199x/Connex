<template>
  <div class="main-body-sub-section">
    <div class="main-body-button-area">
      <q-btn square color="secondary" icon="save" style="margin: 5px 0px 0px; height: 2.5rem; border-radius:5px; " />
    </div>
    <textarea class="my-textarea" wrap="off"/>
    <div class="main-body-button-area" style="flex-direction: row-reverse;">
      <q-btn color="white" text-color="black" label="Send" style="width: 6rem;
        height: 2.5rem;" />
    </div>
  </div>
</template>

<style scoped>
html {
  font-family: sans-serif;
}

.my-textarea {
  flex: auto;
  border-radius: 10px;
  font: italic 1rem small-caps bold;
}
</style>
