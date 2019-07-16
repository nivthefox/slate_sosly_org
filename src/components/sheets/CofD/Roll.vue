<!-- Copyright (c) 2019 Kevin Kragenbrink, II -->
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
  <fieldset class="roll">
    <title>Roll</title>
    <div class="left">
      <select id="roll1" v-model="roll1">
        <option value=""></option>
        <option value="">--ATTRIBUTES--</option>
        <option value="intelligence">Intelligence</option>
        <option value="wits">Wits</option>
        <option value="resolve">Resolve</option>
        <option value="strength">Strength</option>
        <option value="dexterity">Dexterity</option>
        <option value="stamina">Stamina</option>
        <option value="presence">Presence</option>
        <option value="manipulation">Manipulation</option>
        <option value="composure">Composure</option>
        <option value="">--SKILLS--</option>
        <option value="academics">Academics</option>
        <option value="computer">Computer</option>
        <option value="crafts">Crafts</option>
        <option value="investigation">Investigation</option>
        <option value="medicine">Medicine</option>
        <option value="occult">Occult</option>
        <option value="politics">Politics</option>
        <option value="science">Science</option>
        <option value="athletics">Athletics</option>
        <option value="brawl">Brawl</option>
        <option value="drive">Drive</option>
        <option value="firearms">Firearms</option>
        <option value="larceny">Larceny</option>
        <option value="stealth">Stealth</option>
        <option value="survival">Survival</option>
        <option value="weaponry">Weaponry</option>
        <option value="animal_ken">Animal Ken</option>
        <option value="empathy">Empathy</option>
        <option value="expression">Expression</option>
        <option value="intimidation">Intimidation</option>
        <option value="persuasion">Persuasion</option>
        <option value="socialize">Socialize</option>
        <option value="streetwise">Streetwise</option>
        <option value="subterfuge">Subterfuge</option>
      </select><br />
      <select id="roll2" v-model="roll2">
        <option value=""></option>
        <option value="">--ATTRIBUTES--</option>
        <option value="intelligence">Intelligence</option>
        <option value="wits">Wits</option>
        <option value="resolve">Resolve</option>
        <option value="strength">Strength</option>
        <option value="dexterity">Dexterity</option>
        <option value="stamina">Stamina</option>
        <option value="presence">Presence</option>
        <option value="manipulation">Manipulation</option>
        <option value="composure">Composure</option>
        <option value="">--SKILLS--</option>
        <option value="academics">Academics</option>
        <option value="computer">Computer</option>
        <option value="crafts">Crafts</option>
        <option value="investigation">Investigation</option>
        <option value="medicine">Medicine</option>
        <option value="occult">Occult</option>
        <option value="politics">Politics</option>
        <option value="science">Science</option>
        <option value="athletics">Athletics</option>
        <option value="brawl">Brawl</option>
        <option value="drive">Drive</option>
        <option value="firearms">Firearms</option>
        <option value="larceny">Larceny</option>
        <option value="stealth">Stealth</option>
        <option value="survival">Survival</option>
        <option value="weaponry">Weaponry</option>
        <option value="animal_ken">Animal Ken</option>
        <option value="empathy">Empathy</option>
        <option value="expression">Expression</option>
        <option value="intimidation">Intimidation</option>
        <option value="persuasion">Persuasion</option>
        <option value="socialize">Socialize</option>
        <option value="streetwise">Streetwise</option>
        <option value="subterfuge">Subterfuge</option>
      </select><br />
      <select id="roll3" v-model="roll3">
        <option value=""></option>
        <option value="">--ATTRIBUTES--</option>
        <option value="intelligence">Intelligence</option>
        <option value="wits">Wits</option>
        <option value="resolve">Resolve</option>
        <option value="strength">Strength</option>
        <option value="dexterity">Dexterity</option>
        <option value="stamina">Stamina</option>
        <option value="presence">Presence</option>
        <option value="manipulation">Manipulation</option>
        <option value="composure">Composure</option>
        <option value="">--SKILLS--</option>
        <option value="academics">Academics</option>
        <option value="computer">Computer</option>
        <option value="crafts">Crafts</option>
        <option value="investigation">Investigation</option>
        <option value="medicine">Medicine</option>
        <option value="occult">Occult</option>
        <option value="politics">Politics</option>
        <option value="science">Science</option>
        <option value="athletics">Athletics</option>
        <option value="brawl">Brawl</option>
        <option value="drive">Drive</option>
        <option value="firearms">Firearms</option>
        <option value="larceny">Larceny</option>
        <option value="stealth">Stealth</option>
        <option value="survival">Survival</option>
        <option value="weaponry">Weaponry</option>
        <option value="animal_ken">Animal Ken</option>
        <option value="empathy">Empathy</option>
        <option value="expression">Expression</option>
        <option value="intimidation">Intimidation</option>
        <option value="persuasion">Persuasion</option>
        <option value="socialize">Socialize</option>
        <option value="streetwise">Streetwise</option>
        <option value="subterfuge">Subterfuge</option>
    </select><br />
      <label for="mods">Mods</label><input type="number" step="1" id="mods" v-model="mods" /><br />
      <label for="channel">Channel</label>
      <select id="channel" v-model="channel">
        <option v-for="ch in channels" v-bind:value="ch.id">{{ch.name}}</option>
      </select>
    </div>
    <div class="right">
      <label for="again">Again</label><input id="again" type="number" step="1" min="8" max="10" v-model="again" /><br />
      <label for="exceptional">Exceptional</label><input id="exceptional" type="number" step="1" min="1" v-model="exceptional" /><br />
      <label for="rote">Rote</label><input id="rote" type="checkbox" v-model="rote" /><br />
      <label for="rote">Weakness</label><input id="weakness" type="checkbox" v-model="weakness" /><br />
      <label for="rote">Verbose</label><input id="verbose" type="checkbox" v-model="verbose" /><br />
    </div>

    <img class="die" src="@/assets/CofD/roll.png" @click="roll()"/>
  </fieldset>
</template>

<script>
export default {
  name: 'Roll',
  props: ['data'],
  computed: {
    channels() {
      return window.data.channels
    }
  },
  data() {
    return {
      again: 10,
      exceptional: 5,
      verbose: false,
      rote: false,
      weakness: false,
      channel: null,
      roll1: null,
      roll2: null,
      roll3: null,
      mods: 0
    };
  },
  methods: {
    roll() {
      let dice = 0;

      if (this.data.sheet[this.roll1]) {
        dice += this.data.sheet[this.roll1].dots ? this.data.sheet[this.roll1].dots : this.data.sheet[this.roll1];
      }
      if (this.data.sheet[this.roll2]) {
        dice += this.data.sheet[this.roll2].dots ? this.data.sheet[this.roll2].dots : this.data.sheet[this.roll2];
      }
      if (this.data.sheet[this.roll3]) {
        dice += this.data.sheet[this.roll3].dots ? this.data.sheet[this.roll3].dots : this.data.sheet[this.roll3];
      }
      if (this.mods) {
        dice += +this.mods;
      }

      this.$http.post('/api/roll', {
        system: 'cofd',
        again: +this.again || 10,
        exceptional: +this.exceptional || 5,
        verbose: this.verbose,
        rote: this.rote,
        weakness: this.weakness,
        dice: dice,
        channel: this.channel,
      });
    }
  }
}
</script>

<style lang="scss">
fieldset.roll {
  background: white;
  border: 1px solid #CCC;
  border-radius: 10px;
  display: inline-block;
  float: right;
  padding: 10px;
  width: 350px;

  .left {
    float: left;
    width: 50%;
  }

  .right {
    float: right;
    width: 50%;
  }

  title {
    border-bottom: 1px solid #CCC;
    display: block;
    font-weight: bold;
    margin-bottom: 0.5em;
    text-align: center;
  }

  label {
    display: inline-block;
    width: 80px;
  }

  input[type=number] {
    width: 50px;
  }

  img.die {
    cursor: pointer;
    width: 25px;
    float: right;
    vertical-align: middle;
  }
}
</style>