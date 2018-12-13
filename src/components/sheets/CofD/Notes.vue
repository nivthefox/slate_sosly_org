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
  <fieldset class="notes">
    <header>Notes</header>
    <section class="notes-container">
      <div class="note-list">
        <div class="note" v-for="(note, idx) of notes" v-bind:key="idx">
          <div class="tools">
            <i class="fas fa-trash" title="delete this note" @click="notes.splice(idx, 1)" ></i>
            <i v-if="!note.edit" class="fas fa-cogs" title="edit this note" @click="note.edit = !note.edit"></i>
            <i v-if="note.edit" class="fas fa-cogs" title="stop editting this note" @click="note.edit = !note.edit"></i>
          </div>
          <div v-if="!note.edit">
            <h3>{{note.title}}</h3>
            <div class="content" v-html="note.content"></div>
          </div>
          <div v-if="note.edit">
            <input type="text" v-model="note.title" />
            <VueTrix v-model.lazy="note.content" />
          </div>
        </div>
      </div>
    </section>
    <div class="tools">
      <span class="tool add" @click="notes.push({title: 'New Note', content: 'This is the content of your note.', edit: true, collapsed: false})">
        <i class="far fa-plus-square"></i> add a note
      </span>
    </div>
  </fieldset>
</template>

<script>
  import VueTrix from 'vue-trix'

  export default {
  name: 'Notes',
  props: ['notes'],
  components: {
    VueTrix
  }
}
</script>

<style lang="scss">
.notes {
  .tools {
    text-align: right;
    .tool {
      cursor: pointer;
      &:hover {
        &.add {
          color: limegreen;
        }
      }
    }
  }

  .notes-container {
    padding: 0 auto;
    height: 8in;
    overflow-y: scroll;
    overflow-x: hidden;
    width: 7.5in;

    .note-list {
      padding: 0.2in;
      column-count: 2;
      column-gap: 0.1in;
      vertical-align: top;

      .note {
        display: inline-block;
        padding-bottom: 0.1in;
        position: relative;
        vertical-align: top;
        width: 100%;

        h3, input[type="text"] {
          font-family: cursive;
          font-size: 12pt;
          font-weight: bold;
          margin-bottom: 0.1in;
          text-align: left;
          width: 3in;
        }

        trix-toolbar {
          zoom: 0.5;
        }

        trix-editor {
          height: 4in;
          overflow-y: auto;
          overflow-x: hidden;
        }

        .tools {
          text-align: right;
          i {
            cursor: pointer;
            padding-right: 5px;

            &:hover {
              &.fa-trash {
                color: red;
              }
              &.fa-cogs {
                color: blue;
              }
            }
          }
        }
      }
    }
  }
}
</style>