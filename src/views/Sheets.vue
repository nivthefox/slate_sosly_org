<!-- Copyright (c) 2018 Kevin Kragenbrink, II -->
<!-- -->
<!-- Permission is hereby granted, free of charge, to any person obtaining a copy -->
<!-- of this software and associated documentation files (the "Software"), to deal -->
<!-- in the Software without restriction, including without limitation the rights -->
<!-- to use, copy, modify, merge, publish, distribute, sublicense, and/or sell -->
<!-- copies of the Software, and to permit persons to whom the Software is -->
<!-- furnished to do so, subject to the following conditions: -->
<!-- -->
<!-- The above copyright notice and this permission notice shall be included in -->
<!-- all copies or substantial portions of the Software. -->
<!-- -->
<!-- THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR -->
<!-- IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, -->
<!-- FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE -->
<!-- AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER -->
<!-- LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, -->
<!-- OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE -->
<!-- SOFTWARE. -->

<template>
  <article id="characters">
    <header>Characters</header>

    <section class="characters">
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>System</th>
            <!-- <th>Actions</th> //-->
          </tr>
        </thead>
        <tbody>
          <tr v-for="character of characters">
            <td><a v-bind:href="getCharacterURL(character)">{{character.name}}</a></td>
            <td v-text="getSystem(character)"></td>
            <!-- <td>
              <i class="fas fa-trash"></i>
            </td> //-->
          </tr>
        </tbody>
      </table>
    </section>

  </article>
</template>

<script>
  export default {
    name: "characters",
    created() {
      this.$http.get("/api/characters")
        .then((res) => {
          this.characters = res.data
        })
        .catch(() => this.$router.push({path: "/"}))
    },
    data() {
      return {
        characters: []
      }
    },
    methods: {
      getCharacterURL: (character) => `/sheets/${character.id}`,
      getSystem(character) {
        switch(character.system) {
          case 'wtf2e': return "Werewolf: the Forsaken (2nd Edition)";
          case 'cofd2e': return "Chronicles of Darkness (2nd Edition)";
          case 'cofd2e-spirit': return "Chronicles of Darkness Spirit (2nd Edition)";
        }
      }
    }
  }
</script>

<style lang="scss">
  #characters {
    background: white;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2),
    0 6px 20px 0 rgba(0, 0, 0, 0.19);
    box-sizing: border-box;
    margin: 1in auto 0;
    width: 8.5in;

    header {
      background: slategray;
      color: white;
      font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
      font-size: 21pt;
      font-weight: bold;
      text-align: center;
      padding: 0.25in;
      width: 100%;
    }

    .characters {
      padding: 0.25in;
      width: 100%;

      table {
        width: 100%;

        thead {
          th {
            border-bottom: 2px solid slategrey;
            color: dimgrey;
            padding: 0 0.1in;
            text-align: left;

            &:last-of-type {
              text-align: center;
            }
          }
        }

        tbody {
          tr:nth-of-type(odd) {
            background: rgba(0, 0, 0, .1);
          }

          td {
            padding: 0.05in 0.1in;

            a, a:visited {
              color: blue;
            }
          }

          td:last-of-type {
            text-align: center;
          }
        }
      }
    }
  }
</style>