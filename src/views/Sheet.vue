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
    <CofD2e v-if="sheet.system === 'cofd2e'" v-bind:data="sheet"></CofD2e>
    <WtF2e v-if="sheet.system === 'wtf2e'" v-bind:data="sheet"></WtF2e>
  </div>
</template>

<script>
import CofD2e from "../components/sheets/CofD2e.vue";
  import WtF2e from "../components/sheets/WtF2e.vue";

window.data = {sheet: {}};
export default {
  name: "sheet",
  created() {
    this.fetchData();
  },
  data() {
    return window.data;
  },
  watch: {
    sheet: {
      handler(next, prev) {
        if (!prev.id) {
          return;
        }
        this.$http.post(`/api/sheets/${this.$route.params.id}`, next, {
          options: {
            headers: {
              "Content-Type": "application/json"
            }
          }
        });
      },
      deep: true
    }
  },
  methods: {
    fetchData() {
      this.$http.get(`/api/sheets/${this.$route.params.id}`)
        .then((res) => window.data.sheet = res.data)
        .catch(() => this.$router.push({path: "/"}))
    }
  },
  components: {
    CofD2e,
    WtF2e
  }
};
</script>
