<!--
// Copyright (c) 2018 Kevin Kragenbrink, II
//
// Permission is hereby granted, free of charge, to any person obtaining a copy
// of this software and associated documentation files (the "Software"), to deal
// in the Software without restriction, including without limitation the rights
// to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
// copies of the Software, and to permit persons to whom the Software is
// furnished to do so, subject to the following conditions:
//
// The above copyright notice and this permission notice shall be included in
// all copies or substantial portions of the Software.
//
// THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
// IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
// FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
// AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
// LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
// OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
// SOFTWARE.
//-->

<template>
  <fieldset class="attributes" :disabled="locked">
    <header>
      Attributes
      <div class="locks">
        <i v-if="locked" class="fas fa-lock" @click="locked = false"></i>
        <i v-if="!locked" class="fas fa-unlock" @click="locked = true"></i>
      </div>
    </header>
    <table>
      <tr>
        <th>Power</th>
        <td>
          <label for="intelligence">Intelligence</label>
          <DotGroup max="5" min="1" name="intelligence" v-bind:value="data.sheet.intelligence"
                    v-on:dots="data.sheet.intelligence = $event"></DotGroup>
        </td>
        <td>
          <label for="strength">Strength</label>
          <DotGroup max="5" min="1" name="strength" v-bind:value="data.sheet.strength"
                    v-on:dots="data.sheet.strength = $event"></DotGroup>
        </td>
        <td>
          <label for="presence">Presence</label>
          <DotGroup max="5" min="1" name="presence" v-bind:value="data.sheet.presence"
                    v-on:dots="data.sheet.presence = $event"></DotGroup>
        </td>
      </tr>
      <tr>
        <th>Finesse</th>
        <td>
          <label for="wits">Wits</label>
          <DotGroup max="5" min="1" name="wits" v-bind:value="data.sheet.wits"
                    v-on:dots="data.sheet.wits = $event"></DotGroup>
        </td>
        <td>
          <label for="dexterity">Dexterity</label>
          <DotGroup max="5" min="1" name="dexterity" v-bind:value="data.sheet.dexterity"
                    v-on:dots="data.sheet.dexterity = $event"></DotGroup>
        </td>
        <td>
          <label for="manipulation">Manipulation</label>
          <DotGroup max="5" min="1" name="manipulation" v-bind:value="data.sheet.manipulation"
                    v-on:dots="data.sheet.manipulation = $event"></DotGroup>
        </td>
      </tr>
      <tr>
        <th>Resistance</th>
        <td>
          <label for="resolve">Resolve</label>
          <DotGroup max="5" min="1" name="resolve" v-bind:value="data.sheet.resolve"
                    v-on:dots="data.sheet.resolve = $event"></DotGroup>
        </td>
        <td>
          <label for="stamina">Stamina</label>
          <DotGroup max="5" min="1" name="stamina" v-bind:value="data.sheet.stamina"
                    v-on:dots="data.sheet.stamina = $event"></DotGroup>
        </td>
        <td>
          <label for="composure">Composure</label>
          <DotGroup max="5" min="1" name="composure" v-bind:value="data.sheet.composure"
                    v-on:dots="data.sheet.composure = $event"></DotGroup>
        </td>
      </tr>
    </table>
  </fieldset>
</template>

<script>
  import DotGroup from "./DotGroup";

  export default {
    name: "Attributes",
    props: ["data"],
    data() {
      return {
        locked: true
      };
    },
    components: {
      DotGroup
    }
  };
</script>

<style lang="scss">
  .attributes {
    margin-bottom: 0.2in;

    table {
      margin: 0.1in 0 0;
    }
    th {
      border-right-color: black;
      border-right-width: 2px;
      border-right-style: solid;
      color: black;
      font-family: "Treefrog2";
      font-size: 12pt;
      font-weight: normal;
      padding-right: 10px;
      text-align: right;
      vertical-align: top;
    }

    td {
      border-right: 2px solid;
      padding: 0 10px 10px;
      width: 30%;

      &:last-of-type {
        border-right: none;
      }
      .dot-group {
        display: inline-block;
        float: right;
      }
    }

    label {
      display: inline-block;
      font-family: "ArnovaITC TT";
      font-size: 13pt;
    }
  }
</style>