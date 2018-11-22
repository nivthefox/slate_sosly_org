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
  <form id="wtf2e">
    <TOC>
      <a href="#page-1">1</a>
      <a href="#page-2">2</a>
    </TOC>
    <article id="page-1" class="page">
      <header>
        <img src="@/assets/CofD/WtF2e.png"/>
      </header>

      <fieldset class="personal-info">
        <section class="left">
          <div>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" v-model.trim="data.name"/>
          </div>
          <div>
            <label for="player">Player:</label>
            <input type="text" id="player" name="player" v-model.trim="data.userId" disabled/>
          </div>
          <div>
            <label for="chronicle">Chronicle:</label>
            <input type="text" id="chronicle" name="chronicle" v-model.trim="data.sheet.chronicle"/>
          </div>
        </section>
        <section class="middle">
          <div>
            <label for="blood">Blood:</label>
            <input type="text" id="blood" name="blood" v-model.trim="data.sheet.blood"/>
          </div>
          <div>
            <label for="bone">Bone:</label>
            <input type="text" id="bone" name="bone" v-model.trim="data.sheet.bone"/>
          </div>
          <div>
            <label for="concept">Concept:</label>
            <input type="text" id="concept" name="concept" v-model.trim="data.sheet.concept"/>
          </div>
        </section>
        <section class="right">
          <div>
            <label for="auspice">Auspice:</label>
            <input type="text" id="auspice" name="auspice" v-model.trim="data.sheet.auspice"/>
          </div>
          <div>
            <label for="tribe">Tribe:</label>
            <input type="text" id="tribe" name="tribe" v-model.trim="data.sheet.tribe"/>
          </div>
          <div>
            <label for="lodge">Lodge:</label>
            <input type="text" id="lodge" name="lodge" v-model.trim="data.sheet.lodge"/>
          </div>
        </section>
      </fieldset>
      <attributes v-bind:data="data"></attributes>
      <skills v-bind:data="data"></skills>
      <section class="traits">
        <header>Traits</header>

        <merits v-bind:data="data"></merits>
        <fieldset class="health">
          <h1>Health</h1>
          <h2>(+2 Dalu form, +4 Gauru form, +3 Urshul form)</h2>
          <DotGroup min="1" max="20" v-bind:value="data.sheet.health.max"
                    v-on:dots="data.sheet.health.max = $event"></DotGroup>
          <br/>
          <Health v-bind:max="data.sheet.health.max" v-bind:bashing="data.sheet.health.bashing"
                  v-bind:lethal="data.sheet.health.lethal" v-bind:aggravated="data.sheet.health.aggravated"></Health>
        </fieldset>
        <div class="traits-left">
          <fieldset class="renown">
            <h1>Renown</h1>

            <div>
              <label for="cunning">Cunning</label>
              <DotGroup max="5" min="0" v-bind:value="data.sheet.renown.cunning"
                        v-on:dots="data.sheet.renown.cunning = $event"></DotGroup>
            </div>
            <div>
              <label for="glory">Glory</label>
              <DotGroup max="5" min="0" v-bind:value="data.sheet.renown.glory"
                        v-on:dots="data.sheet.renown.glory = $event"></DotGroup>
            </div>
            <div>
              <label for="honor">Honor</label>
              <DotGroup max="5" min="0" v-bind:value="data.sheet.renown.honor"
                        v-on:dots="data.sheet.renown.honor = $event"></DotGroup>
            </div>
            <div>
              <label for="purity">Purity</label>
              <DotGroup max="5" min="0" v-bind:value="data.sheet.renown.purity"
                        v-on:dots="data.sheet.renown.purity = $event"></DotGroup>
            </div>
            <div>
              <label for="wisdom">Wisdom</label>
              <DotGroup max="5" min="0" v-bind:value="data.sheet.renown.wisdom"
                        v-on:dots="data.sheet.renown.wisdom = $event"></DotGroup>
            </div>
          </fieldset>
          <aspirations v-bind:data="data"></aspirations>
        </div>
        <div class="traits-right">
          <fieldset class="willpower">
            <h1>Willpower</h1>
            <DotGroup min="0" v-bind:max="data.sheet.willpower.max" v-bind:value="data.sheet.willpower.current"
                      v-on:dots="data.sheet.willpower.current = $event"></DotGroup>
          </fieldset>
          <fieldset class="primal-urge">
            <h1>Primal Urge</h1>
            <DotGroup min="1" max="10" v-bind:value="data.sheet.primal_urge"
                      v-on:dots="data.sheet.primal_urge = $event"></DotGroup>
          </fieldset>
          <fieldset class="essence">
            <h1>Essence</h1>
            <DotGroup min="0" max="20" newline="10" v-bind:value="data.sheet.essence.current"
                      v-on:dots="data.sheet.essence.current = $event"></DotGroup>
          </fieldset>
          <fieldset class="harmony">
            <h1>Harmony</h1>
            <DotGroup min="1" max="10" v-bind:value="data.sheet.harmony"
                      v-on:dots="data.sheet.harmony = $event"></DotGroup>
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
          <input type="number" v-model="data.sheet.experiences"/>
        </fieldset>
      </section>
    </article>
    <article id="page-2" class="page">
      <header>
        <img src="@/assets/CofD/WtF2e.png"/>
      </header>
    </article>
  </form>
</template>

<script>
  import Aspirations from "./CofD/Aspirations";
  import Attributes from "./CofD/Attributes";
  import DotGroup from "./CofD/DotGroup";
  import Health from "./CofD/Health";
  import Merits from "./CofD/Merits";
  import Skills from "./CofD/Skills";
  import TOC from "./TOC";

  export default {
    name: "WtF2e",
    props: ["data"],
    components: {
      Aspirations,
      Attributes,
      DotGroup,
      Health,
      Merits,
      Skills,
      TOC
    }
  };
</script>

<style lang="scss">
  @import "sass/cofd";
  @import "../../assets/fonts/wtf2e.css";

  $brown: saddlebrown;
  $pencil: #333333;

  #wtf2e {
    zoom: 1;

    margin: 0 auto;
    padding: 0.5in 0;
    position: relative;
    width: 8.5in;

    .page {
      background-image: url('../../assets/CofD/forsaken-background.jpg');
      background-size: 100% 100%;

      &:before {
        background-color: $brown;
        mask-image: url("../../assets/CofD/forsaken-skull.png");
        mask-position: center center;
        mask-repeat: no-repeat, no-repeat;
        opacity: 0.2;
      }
      & > section, & > fieldset {
        header {
          color: $brown;
          font-family: "Flat Earth Scribe";
          text-align: center;
          text-transform: uppercase;
          width: 100%;
        }

        h1, h2 {
          text-align: center;
          font-weight: normal;
        }

        h1 {
          color: $brown;
          font-family: "Treefrog2";
          font-size: 14pt;
        }

        h2 {
          font-family: Skia;
          font-size: 7pt;
          font-style: italic;
          padding-bottom: 0.1in;
        }
      }

      .personal-info {
        input {
          // middle
          &#blood {
            width: 154px;
          }
          &#bone {
            width: 158px;
          }

          // right
          &#auspice {
            width: 133px;
          }
          &#tribe {
            width: 148px;
          }
          &#lodge {
            width: 148px;
          }
        }

        label {
          color: $brown;
          font-family: "Treefrog2";
          font-size: 15pt;
        }
      }
      .attributes {
        th {
          border-right-color: $brown;
          color: $brown;
        }
        td {
          border-right-color: $brown;
        }
      }
      .skills {
        & > div {
          border-right-color: $brown;
        }
      }
      .traits {
        display: inline-block;
        float: right;
        padding-left: 0;
        vertical-align: top;
        width: 50%;
      }
      .renown {
        label {
          font-family: "ArnovaITC TT";
          font-size: 13pt;
        }

        .dot-group {
          float: right;
        }
      }
      .aspirations {
        input {
          text-align: center;
          width: 100%;
        }
      }
      .traits-left, .traits-right {
        float: left;
        width: 50%;
      }
      .willpower, .essence, .primal-urge, .harmony, .renown, .aspirations {
        padding: 0 0.1in;
        h1 {
          margin-bottom: 0.1in;
        }
      }
      .willpower, .primal-urge, .essence, .harmony  {
        text-align: center;
      }
      fieldset.health {
        margin-top: 0.2in;
        text-align: center;
      }
      .experience {
        padding: 0.1in;
        display: inline-block;
        width: 50%;

        .beats, .experiences {
          display:  inline-block;
          width: 50%;

          .dot-group {
            float: right;

            .dot span {
              border-radius: 0;
            }
          }

          input {
            width: 4em;
            text-align: right;
            padding: 0;
          }

          label {
            font-family: "ArnovaITC TT";
            font-size: 13pt;
          }
        }
        .experiences { text-align: center; }
      }
    }
  }
</style>
