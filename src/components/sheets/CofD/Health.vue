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
    <span class="health">
      <span v-for="(health, i) of dots" v-bind:key="i" class="box">
        <i class="fas fa-asterisk" v-if="isAggravated(i)"></i>
        <i class="fas fa-times" v-if="isLethal(i)"></i>
        <i class="fas fa-slash" v-if="isBashing(i)"></i>
      </span>
    </span>
</template>

<script>
  export default {
    name: "Health",
    props: ["max", "bashing", "lethal", "aggravated"],
    computed: {
      dots: function () {
        const arr = [];
        for (let i = 0; i < this.max; i++) {
          arr.push(i);
        }
        return arr;
      }
    },
    methods: {
      isAggravated: function (i) {
        return i < this.aggravated;
      },
      isLethal: function(i) {
        const offset = this.aggravated;
        return i >= offset && (i - offset) < this.lethal;
      },
      isBashing: function(i) {
        const offset = this.aggravated + this.lethal;
        return i >= offset && (i - offset) < this.bashing;
      }
    }
  };
</script>

<style lang="scss">
  span.health {
    display: inline-block;
    margin-top: 5px;

    .box {
      border: 1px solid black;
      color: #333;
      display: inline-block;
      height: 13px;
      margin: 0 2px;
      width: 13px;
      vertical-align: top;

      .fas { vertical-align: top; }
      .fa-asterisk { font-size: 9pt; }
      .fa-times { font-size: 11pt; }
      .fa-slash { font-size: 9pt; }
    }
  }
</style>
