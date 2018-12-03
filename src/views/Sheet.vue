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
  <div class="sheet">
    <CofD2e v-if="sheet.type === 'cofd2e'" v-bind:data="sheet"></CofD2e>
    <WtF2e v-if="sheet.type === 'wtf2e'" v-bind:data="sheet"></WtF2e>
  </div>
</template>

<script>
import CofD2e from "@/components/sheets/CofD2e.vue";
import WtF2e from "@/components/sheets/WtF2e.vue";

export default {
  name: "sheet",
  created: function () {
      this.fetchData();
  },
  data: function() {
    window.data = window.data || {sheet: {}};
    return window.data;
  },
  methods: {
    fetchData: function () {
      this.$http.get('https://slatebot-dev.herokuapps.com/sheets/1069722894365364224')
        .then((res) => {
          window.data = res.data;
        });
    }
  },
  components: {
    CofD2e,
    WtF2e
  }
};
</script>
