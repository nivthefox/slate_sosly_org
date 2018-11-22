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
  <fieldset class="skills">
    <header>Skills</header>
    <div class="mental">
      <h1>Mental</h1>
      <h2>(-3 Unskilled)</h2>

      <div>
        <label for="academics">Academics</label>
        <DotGroup max="5" min="0" name="academics" v-bind:value="data.sheet.academics.dots" v-on:dots="data.sheet.academics.dots = $event"></DotGroup>
        <input type="text" id="academics" v-model="data.sheet.academics.specialties" />
      </div>
      <div>
        <label for="computer">Computer</label>
        <DotGroup max="5" min="0" name="computer" v-bind:value="data.sheet.computer.dots" v-on:dots="data.sheet.computer.dots = $event"></DotGroup>
        <input type="text" id="computer" v-model="data.sheet.computer.specialties" />
      </div>
      <div>
        <label for="crafts">Crafts</label>
        <DotGroup max="5" min="0" name="crafts" v-bind:value="data.sheet.crafts.dots" v-on:dots="data.sheet.crafts.dots = $event"></DotGroup>
        <input type="text" id="crafts" v-model="data.sheet.crafts.specialties" />
      </div>
      <div>
        <label for="investigation">Investigation</label>
        <DotGroup max="5" min="0" name="investigation" v-bind:value="data.sheet.investigation.dots" v-on:dots="data.sheet.investigation.dots = $event"></DotGroup>
        <input type="text" id="investigation" v-model="data.sheet.investigation.specialties" />
      </div>
      <div>
        <label for="medicine">Medicine</label>
        <DotGroup max="5" min="0" name="medicine" v-bind:value="data.sheet.medicine.dots" v-on:dots="data.sheet.medicine.dots = $event"></DotGroup>
        <input type="text" id="medicine" v-model="data.sheet.medicine.specialties" />
      </div>
      <div>
        <label for="occult">Occult</label>
        <DotGroup max="5" min="0" name="occult" v-bind:value="data.sheet.occult.dots" v-on:dots="data.sheet.occult.dots = $event"></DotGroup>
        <input type="text" id="occult" v-model="data.sheet.occult.specialties" />
      </div>
      <div>
        <label for="politics">Politics</label>
        <DotGroup max="5" min="0" name="politics" v-bind:value="data.sheet.politics.dots" v-on:dots="data.sheet.politics.dots = $event"></DotGroup>
        <input type="text" id="politics" v-model="data.sheet.politics.specialties" />
      </div>
      <div>
        <label for="science">Science</label>
        <DotGroup max="5" min="0" name="science" v-bind:value="data.sheet.science.dots" v-on:dots="data.sheet.science.dots = $event"></DotGroup>
        <input type="text" id="science" v-model="data.sheet.science.specialties" />
      </div>
    </div>
    <div class="physical">
      <h1>Physical</h1>
      <h2>(-1 Unskilled)</h2>

      <div>
        <label for="athletics">Athletics</label>
        <DotGroup max="5" min="0" name="athletics" v-bind:value="data.sheet.athletics.dots" v-on:dots="data.sheet.athletics.dots = $event"></DotGroup>
        <input type="text" id="athletics" v-model="data.sheet.athletics.specialties" />
      </div>
      <div>
        <label for="brawl">Brawl</label>
        <DotGroup max="5" min="0" name="brawl" v-bind:value="data.sheet.brawl.dots" v-on:dots="data.sheet.brawl.dots = $event"></DotGroup>
        <input type="text" id="brawl" v-model="data.sheet.brawl.specialties" />
      </div>
      <div>
        <label for="drive">Drive</label>
        <DotGroup max="5" min="0" name="drive" v-bind:value="data.sheet.drive.dots" v-on:dots="data.sheet.drive.dots = $event"></DotGroup>
        <input type="text" id="drive" v-model="data.sheet.drive.specialties" />
      </div>
      <div>
        <label for="firearms">Firearms</label>
        <DotGroup max="5" min="0" name="firearms" v-bind:value="data.sheet.firearms.dots" v-on:dots="data.sheet.firearms.dots = $event"></DotGroup>
        <input type="text" id="firearms" v-model="data.sheet.firearms.specialties" />
      </div>
      <div>
        <label for="larceny">Larceny</label>
        <DotGroup max="5" min="0" name="larceny" v-bind:value="data.sheet.larceny.dots" v-on:dots="data.sheet.larceny.dots = $event"></DotGroup>
        <input type="text" id="larceny" v-model="data.sheet.larceny.specialties" />
      </div>
      <div>
        <label for="stealth">Stealth</label>
        <DotGroup max="5" min="0" name="stealth" v-bind:value="data.sheet.stealth.dots" v-on:dots="data.sheet.stealth.dots = $event"></DotGroup>
        <input type="text" id="stealth" v-model="data.sheet.stealth.specialties" />
      </div>
      <div>
        <label for="survival">Survival</label>
        <DotGroup max="5" min="0" name="survival" v-bind:value="data.sheet.survival.dots" v-on:dots="data.sheet.survival.dots = $event"></DotGroup>
        <input type="text" id="survival" v-model="data.sheet.survival.specialties" />
      </div>
      <div>
        <label for="weaponry">Weaponry</label>
        <DotGroup max="5" min="0" name="weaponry" v-bind:value="data.sheet.weaponry.dots" v-on:dots="data.sheet.weaponry.dots = $event"></DotGroup>
        <input type="text" id="weaponry" v-model="data.sheet.weaponry.specialties" />
      </div>
    </div>

    <div class="social">
      <h1>Social</h1>
      <h2>(-1 Unskilled)</h2>

      <div>
        <label for="animal_ken">Animal Ken</label>
        <DotGroup max="5" min="0" name="animal_ken" v-bind:value="data.sheet.animal_ken.dots" v-on:dots="data.sheet.animal_ken.dots = $event"></DotGroup>
        <input type="text" id="animal_ken" v-model="data.sheet.animal_ken.specialties" />
      </div>
      <div>
        <label for="empathy">Empathy</label>
        <DotGroup max="5" min="0" name="empathy" v-bind:value="data.sheet.empathy.dots" v-on:dots="data.sheet.empathy.dots = $event"></DotGroup>
        <input type="text" id="empathy" v-model="data.sheet.empathy.specialties" />
      </div>
      <div>
        <label for="expression">Expression</label>
        <DotGroup max="5" min="0" name="expression" v-bind:value="data.sheet.expression.dots" v-on:dots="data.sheet.expression.dots = $event"></DotGroup>
        <input type="text" id="expression" v-model="data.sheet.expression.specialties" />
      </div>
      <div>
        <label for="intimidation">Intimidation</label>
        <DotGroup max="5" min="0" name="intimidation" v-bind:value="data.sheet.intimidation.dots" v-on:dots="data.sheet.intimidation.dots = $event"></DotGroup>
        <input type="text" id="intimidation" v-model="data.sheet.intimidation.specialties" />
      </div>
      <div>
        <label for="persuasion">Persuasion</label>
        <DotGroup max="5" min="0" name="persuasion" v-bind:value="data.sheet.persuasion.dots" v-on:dots="data.sheet.persuasion.dots = $event"></DotGroup>
        <input type="text" id="persuasion" v-model="data.sheet.persuasion.specialties" />
      </div>
      <div>
        <label for="socialize">Socialize</label>
        <DotGroup max="5" min="0" name="socialize" v-bind:value="data.sheet.socialize.dots" v-on:dots="data.sheet.socialize.dots = $event"></DotGroup>
        <input type="text" id="socialize" v-model="data.sheet.socialize.specialties" />
      </div>
      <div>
        <label for="streetwise">Streetwise</label>
        <DotGroup max="5" min="0" name="streetwise" v-bind:value="data.sheet.streetwise.dots" v-on:dots="data.sheet.streetwise.dots = $event"></DotGroup>
        <input type="text" id="streetwise" v-model="data.sheet.streetwise.specialties" />
      </div>
      <div>
        <label for="subterfuge">Subterfuge</label>
        <DotGroup max="5" min="0" name="subterfuge" v-bind:value="data.sheet.subterfuge.dots" v-on:dots="data.sheet.subterfuge.dots = $event"></DotGroup>
        <input type="text" id="subterfuge" v-model="data.sheet.subterfuge.specialties" />
      </div>
    </div>
  </fieldset>
</template>

<script>
  import DotGroup from "./DotGroup";

  export default {
    name: "Skills",
    props: ["data"],
    methods: {
      fix: function(input) {
        console.log(this.data.sheet[input].specialties);
      }
    },
    components: {
      DotGroup
    }
  };
</script>
<style lang="scss">
  .skills {
    display: inline-block;
    float: left;
    padding-right: 0;
    vertical-align: top;
    width: 50%;

    & > div {
      border-right-color: black;
      border-right-style: solid;
      border-right-width: 2px;
      padding-right: 0.1in;
      padding-top: 0.2in;

      &:first-of-type {
        margin-top: 0.2in;
        padding-top: 0;
      }

      label {
        display: inline-block;
        font-family: "ArnovaITC TT";
        font-size: 13pt;
      }

      input[type="text"] {
        float: right;
        text-align: left;
      }

      .dot-group {
        float: right;
      }
    }
  }
</style>