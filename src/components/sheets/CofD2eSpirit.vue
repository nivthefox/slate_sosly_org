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
  <form id="cofd2espirit">
    <article id="page-1" class="page">
      <div class="overlay"></div>
      <header>
        <img src="@/assets/CofD/CofD2e.png" />
      </header>

      <fieldset class="personal-info">
        <section class="left">
          <div>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" v-model.trim.lazy="data.name"/>
          </div>
          <div>
            <label for="concept">Concept:</label>
            <input type="text" id="concept" name="concept" v-model.trim.lazy="data.sheet.concept"/>
          </div>
        </section>
        <section class="middle">
          <div>
            <label for="virtue">Virtue:</label>
            <input type="text" id="virtue" name="virtue" v-model.trim.lazy="data.sheet.virtue"/>
          </div>
          <div>
            <label for="vice">Vice:</label>
            <input type="text" id="vice" name="vice" v-model.trim.lazy="data.sheet.vice"/>
          </div>
        </section>
        <section class="right">
          <div>
            <label for="type">Type:</label>
            <input type="text" id="type" name="type" v-model.trim.lazy="data.sheet.type"/>
          </div>
          <div>
            <label for="rank">Rank:</label>
            <input type="text" id="rank" name="rank" v-model.trim.lazy="data.sheet.rank"/>
          </div>
        </section>
      </fieldset>
      <section class="left">
        <fieldset class="attributes">
          <header>Attributes</header>
          <div>
            <label for="power">Power</label>
            <DotGroup max="10" min="1" name="power" v-bind:value="data.sheet.power"
              v-on:dots="data.sheet.power = $event"></DotGroup>
          </div>
          <div>
            <label for="finesse">Finesse</label>
            <DotGroup max="10" min="1" name="finesse" v-bind:value="data.sheet.finesse"
              v-on:dots="data.sheet.finesse = $event"></DotGroup>
          </div>
          <div>
            <label for="resistance">Resistance</label>
            <DotGroup max="10" min="1" name="resistance" v-bind:value="data.sheet.resistance"
              v-on:dots="data.sheet.resistance = $event"></DotGroup>
          </div>
        </fieldset>
        <fieldset class="traits">
          <header>Other Traits</header>
          <div class="corpus">
            <label for="health">Corpus</label>
            <DotGroup min="1" max="20" newline="10" v-bind:value="data.sheet.health.max"
                      v-on:dots="data.sheet.health.max = $event"></DotGroup>
            <br/>
            <Health v-bind:health="data.sheet.health"></Health>
          </div>
          <div class="willpower">
            <label for="willpower">Willpower</label>
            <DotGroup min="0" v-bind:max="(data.sheet.resistance + data.sheet.power)"
              v-bind:value="data.sheet.willpower.current"
              v-on:dots="data.sheet.willpower.current = $event"></DotGroup>
          </div>
          <div class="essence">
            <label for="essence">Essence</label>
            <input type="number" v-bind="data.sheet.essence.current" />
            /
            <input type="number" v-bind="data.sheet.essence.max" />
          </div>
          <div class="integrity">
            <label for="integrity">Integrity</label>
            <DotGroup min="0" v-bind:max="10"
              v-bind:value="data.sheet.integrity"
              v-on:dots="data.sheet.integrity = $event"></DotGroup>
          </div>
        </fieldset>
        <fieldset class="numina">
          <label for="numina">Numina</label>
          <div class="wrapper">
            <div class="list">
              <div class="numen" v-for="(_, idx) of data.sheet.numina" v-bind:key="idx">
                <input type="text" v-model.trim.lazy="data.sheet.numina[idx]" />
                <i class="far fa-minus-square" @click="data.sheet.numina.splice(idx, 1)"></i>
              </div>
            </div>
          </div>
          <div class="control">
            <span title="add a numen" @click="data.sheet.numina.push('')"><i class="far fa-plus-square"></i> add a numen</span>
          </div>
        </fieldset>
        <fieldset class="anchors">
          <label for="anchors">Anchors</label>
          <div class="wrapper">
            <div class="list">
              <div class="anchor" v-for="(_, idx) of data.sheet.anchors" v-bind:key="idx">
                <input type="text" v-model.trim.lazy="data.sheet.anchors[idx]" />
                <i class="far fa-minus-square" @click="data.sheet.anchors.splice(idx, 1)"></i>
              </div>
            </div>
          </div>
          <div class="control">
            <span title="add an anchor" @click="data.sheet.anchors.push('')"><i class="far fa-plus-square"></i> add an anchor</span>
          </div>
        </fieldset>
      </section>
      <section class="right">

      </section>
    </article>
  </form>
</template>

<script>
  import DotGroup from "./CofD/DotGroup"
  import Health from "./CofD/Health"

  export default {
    name: "CofD2eSpirit",
    props: ["data"],
    components: {
      DotGroup,
      Health
    }
  }
</script>

<style lang="scss">
  @import "sass/basecofd";
  @import "sass/cofd2espirit";
  @import "../../assets/fonts/cofd2e.css";
</style>