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
  <fieldset class="merits">
    <h1>Merits</h1>

    <div class="merit-list">
      <div class="merit" v-for="(merit, idx) of data.sheet.merits" v-bind:key="idx">
        <input type="text" v-model.trim.lazy="merit.name" />
        <DotGroup max="5" min="0" v-bind:value="merit.dots" v-on:dots="merit.dots = $event"></DotGroup>
        <i class="far fa-minus-square" @click="data.sheet.merits.splice(idx, 1)"></i>
      </div>
    </div>
    <div class="control">
      <span title="add a merit" @click="data.sheet.merits.push({name: '', dots: 0})"><i class="far fa-plus-square"></i>add a merit</span>
    </div>
  </fieldset>
</template>

<style lang="scss">
  fieldset.merits {
    padding-left: 0.1in;
    padding-top: 0.2in;

    div.merit-list {
      height: 11em;
      overflow-y: auto;
      overflow-x: hidden;

      div.merit {
        input[type="text"] {
          text-align: left;
          width: 250px;
        }

        i.fa-minus-square {
          margin-left: 0.5em;
          cursor: pointer;

          &:hover {
            color: red;
          }
        }
      }
    }

    div.control {
      text-align: right;

      span {
        color: black;
        cursor: pointer;
        &:hover {
          color: limegreen;
        }

        i {
          margin-right: 0.5em;
        }
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