<template>
  <fieldset class="merits">
    <h1>Merits</h1>

    <div v-for="(merit, idx) of data.sheet.merits" v-bind:key="idx">
      <input type="text" v-model="merit.name" />
      <DotGroup max="5" min="0" v-bind:value="merit.dots" v-on:dots="merit.dots = $event"></DotGroup>
    </div>
  </fieldset>
</template>

<style lang="scss">
  fieldset.merits {
    padding-left: 0.1in;
    padding-top: 0.2in;

    div {
      input[type="text"] {
        text-align: left;
        width: 290px;
      }
    }
  }
</style>
<script>
  import DotGroup from "./DotGroup";
  export default {
    name: 'Merits',
    props: ['data'],
    components: {DotGroup}
  }
</script>