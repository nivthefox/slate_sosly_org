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
  <div id="app">
    <reset />
    <navigation v-if="auth.isAuthenticated" v-bind:auth="auth" />
    <router-view v-bind:auth="auth" />
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.5.0/css/all.css"
          integrity="sha384-B4dIYHKNBt8Bc12p+WXckhzcICo0wtJAoU8YZTY5qE0Id1GSseTk6S+L3BlXeVIU" crossorigin="anonymous">
  </div>
</template>

<script>
  import Reset from "./components/Reset.vue"; // imported first to cascade
  import Navigation from "./components/Navigation.vue";

  export default {
    name: "app",
    created() {
      this.$http.get("/api/auth")
        .then((auth) => {
          this.auth.isAuthenticated = (auth.id !== 0);
          this.auth.user = auth;
        })
        .catch((err) => {
          this.auth.isAuthenticated = false;
          this.auth.user = null;
          console.log(err);
        });
    },
    data() {
      return {
        auth: {
          isAuthenticated: false,
          user: null
        }
      };
    },
    methods: {
      isAuthenticated() {

      }
    },
    components: {
      Navigation,
      Reset
    }
  };
</script>

<style lang="scss">
  #app {
    background: rgb(82, 86, 89);
    left: 0;
    min-height: 100%;
    padding: 0.5in 0;
    position: absolute;
    top: 0;
    width: 100%;
  }
</style>
