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
    <span class="dot-group">
        <i class="fas fa-ban" v-if="this.min === '0'" v-on:click="$emit('dots', 0)"></i>
        <span class="dot-container" v-for="(_, dot) in dots" v-bind:key="dot">
          <span class="dot">
              <input type="radio" v-bind:name="name" v-bind:id="name" v-bind:value="dot + 1" v-model="ivalue"
                     v-on:click="$emit('dots', dot + 1)"/>
              <span class="filled" v-if="value >= dot + 1"></span>
              <span class="empty" v-if="value < dot + 1"></span>
          </span>
          <br v-if="newline == dot + 1" />
        </span>
    </span>
</template>

<script>
  export default {
    name: "DotGroup",
    props: ["newline", "max", "min", "name", "value"],
    data: function () {
      return {ivalue: this.value};
    },
    computed: {
      dots: function () {
        const arr = [];
        for (let i = 0; i < this.max; i++) {
          arr.push(i < this.value);
        }
        return arr;
      }
    }
  };
</script>

<style lang="scss">
  .dot-group {
    .fa-ban {
      color: #CCC;
      font-size: 11px;
      padding-top: 2px;
      vertical-align: top;

      &:hover {
        color: red;
        cursor: pointer;
      }
    }

    .dot {
      cursor: pointer;
      display: inline-block;
      height: 11px;
      -webkit-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      margin: 0 1px;
      position: relative;
      user-select: none;
      width: 11px;

      &:hover input[type="radio"] ~ span {
        background: lightgrey;
      }

      input[type="radio"] {
        cursor: pointer;
        left: 0;
        margin: 0;
        opacity: 0;
        padding: 0;
        position: absolute;
        top: 0;
      }

      span {
        background: #fff;
        border: 1px solid black;
        border-radius: 50%;
        display: block;
        height: 11px;
        left: 0;
        pointer-events: none;
        position: absolute;
        top: 0;
        width: 11px;

        &.filled {
          background: black;
        }

        &:after {
          color: #444;
          counter-increment: radio-group;
          content: counter(radio-group);
          font-size: 5pt;
          left: 0;
          opacity: 0;
          position: absolute;
          text-align: center;
          top: 1px;
          width: 9px;
        }
      }
    }
  }
</style>
