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
    <form id="cofd2e">
        <article id="page-1" class="page">
            <header>
                <img src="@/assets/CofD/CofD2e.png"/>
            </header>

            <fieldset class="personal-info">
                <section class="left">
                    <div>
                        <label for="name">Name:</label>
                        <input type="text" id="name" name="name" v-model.trim.lazy="data.name"/>
                    </div>
                    <div>
                        <label for="playerName">Player:</label>
                        <input type="text" id="playerName" name="playerName" v-model.trim="data.playerName" disabled/>
                    </div>
                    <div>
                        <label for="chronicle">Chronicle:</label>
                        <input type="text" id="chronicle" name="chronicle" v-model.trim.lazy="data.sheet.chronicle"/>
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
                    <div>
                        <label for="concept">Concept:</label>
                        <input type="text" id="concept" name="concept" v-model.trim.lazy="data.sheet.concept"/>
                    </div>
                </section>
                <section class="right">
                    <div>
                        <label for="faction">Faction:</label>
                        <input type="text" id="faction" name="faction" v-model.trim.lazy="data.sheet.faction"/>
                    </div>
                    <div>
                        <label for="group">Group:</label>
                        <input type="text" id="group" name="group" v-model.trim.lazy="data.sheet.group"/>
                    </div>
                    <div>
                        <label for="template">Template:</label>
                        <input type="text" id="template" name="template" v-model.trim.lazy="data.sheet.template"/>
                    </div>
                </section>
            </fieldset>
            <attributes v-bind:data="data"></attributes>
            <skills v-bind:data="data"></skills>
            <section class="traits">
                <header>Traits</header>

                <merits v-bind:data="data"></merits>
                <div class="traits-left">
                    <fieldset class="conditions">
                      <h1>Conditions</h1>
                      <textarea v-model.trim.lazy="data.sheet.conditions"></textarea>
                    </fieldset>
                    <aspirations v-bind:data="data"></aspirations>
                </div>
                <div class="traits-right">
                  <fieldset class="health">
                    <h1>Health</h1>
                    <DotGroup min="1" max="20" newline="10" v-bind:value="data.sheet.health.max"
                              v-on:dots="data.sheet.health.max = $event"></DotGroup>
                    <br/>
                    <Health v-bind:health="data.sheet.health"></Health>
                  </fieldset>
                    <fieldset class="willpower">
                        <h1>Willpower</h1>
                        <DotGroup min="0" v-bind:max="(data.sheet.resolve + data.sheet.composure)" v-bind:value="data.sheet.willpower.current"
                                  v-on:dots="data.sheet.willpower.current = $event"></DotGroup>
                    </fieldset>
                    <fieldset class="integrity">
                        <h1>Integrity</h1>
                        <DotGroup min="1" max="10" v-bind:value="data.sheet.integrity"
                                  v-on:dots="data.sheet.integrity = $event"></DotGroup>
                    </fieldset>
                </div>
            </section>
            <section class="experience">
                <fieldset class="beats">
                    <label>Beats</label>
                    <DotGroup min="0" max="5" v-bind:value="data.sheet.beats" v-on:dots="data.sheet.beats = $event"></DotGroup>
                </fieldset>
                <fieldset class="experiences">
                    <label>Experiences</label>
                    <input type="number" v-model.number="data.sheet.experiences"/>
                </fieldset>
            </section>
        </article>

        <article id="page-3" class="page">
            <header>
              <img src="@/assets/CofD/CofD2e.png"/>
            </header>
            <Notes v-bind:notes="data.sheet.notes"></Notes>
        </article>
    </form>
</template>

<script>
  import Aspirations from "./CofD/Aspirations";
  import Attributes from "./CofD/Attributes";
  import DotGroup from "./CofD/DotGroup";
  import Health from "./CofD/Health";
  import Merits from "./CofD/Merits";
  import Notes from "./CofD/Notes";
  import Skills from "./CofD/Skills";
  import TOC from "./TOC";

  export default {
    name: "CofD2e",
    props: ["data"],
    components: {
      Aspirations,
      Attributes,
      DotGroup,
      Health,
      Merits,
      Notes,
      Skills,
      TOC
    }
  };
</script>

<style lang="scss">
@import "sass/basecofd";
@import "sass/cofd2e";
@import "../../assets/fonts/cofd2e.css";
</style>
