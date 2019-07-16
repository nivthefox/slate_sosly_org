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
      <a href="#page-3">3</a>
    </TOC>
    <article id="page-1" class="page">
      <header>
        <img src="@/assets/CofD/WtF2e.png"/>
        <roll v-bind:data="data"></roll>
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
            <label for="blood">Blood:</label>
            <input type="text" id="blood" name="blood" v-model.trim.lazy="data.sheet.blood"/>
          </div>
          <div>
            <label for="bone">Bone:</label>
            <input type="text" id="bone" name="bone" v-model.trim.lazy="data.sheet.bone"/>
          </div>
          <div>
            <label for="concept">Concept:</label>
            <input type="text" id="concept" name="concept" v-model.trim.lazy="data.sheet.concept"/>
          </div>
        </section>
        <section class="right">
          <div>
            <label for="auspice">Auspice:</label>
            <input type="text" id="auspice" name="auspice" v-model.trim.lazy="data.sheet.auspice"/>
          </div>
          <div>
            <label for="tribe">Tribe:</label>
            <input type="text" id="tribe" name="tribe" v-model.trim.lazy="data.sheet.tribe"/>
          </div>
          <div>
            <label for="lodge">Lodge:</label>
            <input type="text" id="lodge" name="lodge" v-model.trim.lazy="data.sheet.lodge"/>
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
          <DotGroup min="1" max="20" newline="10" v-bind:value="data.sheet.health.max"
                    v-on:dots="data.sheet.health.max = $event"></DotGroup>
          <br/>
          <Health v-bind:health="data.sheet.health"></Health>
        </fieldset>
        <div class="traits-left">
          <fieldset class="renown" :disabled="locks.renown">
            <h1>
              Renown
              <div class="locks">
                <i v-if="locks.renown" class="fas fa-lock" @click="locks.renown = false"></i>
                <i v-if="!locks.renown" class="fas fa-unlock" @click="locks.renown = true"></i>
              </div>
            </h1>

            <div>
              <label for="cunning">Cunning</label>
              <DotGroup id="cunning" max="5" min="0" v-bind:value="data.sheet.cunning"
                        v-on:dots="data.sheet.cunning = $event"></DotGroup>
            </div>
            <div>
              <label for="glory">Glory</label>
              <DotGroup id="glory" max="5" min="0" v-bind:value="data.sheet.glory"
                        v-on:dots="data.sheet.glory = $event"></DotGroup>
            </div>
            <div>
              <label for="honor">Honor</label>
              <DotGroup id="honor" max="5" min="0" v-bind:value="data.sheet.honor"
                        v-on:dots="data.sheet.honor = $event"></DotGroup>
            </div>
            <div>
              <label for="purity">Purity</label>
              <DotGroup id="purity" max="5" min="0" v-bind:value="data.sheet.purity"
                        v-on:dots="data.sheet.purity = $event"></DotGroup>
            </div>
            <div>
              <label for="wisdom">Wisdom</label>
              <DotGroup id="wisdom" max="5" min="0" v-bind:value="data.sheet.wisdom"
                        v-on:dots="data.sheet.wisdom = $event"></DotGroup>
            </div>
          </fieldset>
          <aspirations v-bind:data="data"></aspirations>
        </div>
        <div class="traits-right">
          <fieldset class="willpower">
            <h1>Willpower</h1>
            <DotGroup min="0" v-bind:max="(data.sheet.resolve + data.sheet.composure)" v-bind:value="data.sheet.willpower.current"
                      v-on:dots="data.sheet.willpower.current = $event"></DotGroup>
          </fieldset>
          <fieldset class="primal-urge" :disabled="locks.primalUrge">
            <h1>
              Primal Urge
              <div class="locks">
                <i v-if="locks.primalUrge" class="fas fa-lock" @click="locks.primalUrge = false"></i>
                <i v-if="!locks.primalUrge" class="fas fa-unlock" @click="locks.primalUrge = true"></i>
              </div>
            </h1>
            <DotGroup min="1" max="10" v-bind:value="data.sheet.primal_urge"
                      v-on:dots="data.sheet.primal_urge = $event"></DotGroup>
          </fieldset>
          <fieldset class="essence">
            <h1>Essence</h1>
            <DotGroup min="0" max="20" newline="10" v-bind:value="data.sheet.essence.current"
                      v-on:dots="data.sheet.essence.current = $event"></DotGroup>
          </fieldset>
          <fieldset class="harmony" :disabled="locks.harmony">
            <h1>
              Harmony
              <div class="locks">
                <i v-if="locks.harmony" class="fas fa-lock" @click="locks.harmony = false"></i>
                <i v-if="!locks.harmony" class="fas fa-unlock" @click="locks.harmony = true"></i>
              </div>
            </h1>
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
          <input type="number" v-model.number="data.sheet.experiences"/>
        </fieldset>
      </section>
    </article>
    <article id="page-2" class="page">
      <header>
        <img src="@/assets/CofD/WtF2e.png" />
      </header>
      <fieldset class="forms">
        <section>
          <h1>Hishu</h1>
          <h2>(Human)</h2>
          <div>
            <label>Strength:</label>
            <span>{{ data.sheet.strength }}</span>
          </div>
          <div>
            <label>Dexterity:</label>
            <span>{{ data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Stamina:</label>
            <span>{{ data.sheet.stamina }}</span>
          </div>
          <div>
            <label>Manipulation:</label>
            <span>{{ data.sheet.manipulation }}</span>
          </div>
          <div>&nbsp;</div>
          <div>
            <label>Size:</label>
            <input type="number" v-model="data.sheet.size" />
          </div>
          <div>
            <label>Defense:</label>
            <span>{{ data.sheet.wits > data.sheet.dexterity ? data.sheet.dexterity : data.sheet.wits }}</span>
          </div>
          <div>
            <label>Initiative:</label>
            <span>{{ data.sheet.wits + data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Speed:</label>
            <span>{{ parseInt(data.sheet.size) + data.sheet.strength + data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Perception:</label>
            <span>+1</span>
          </div>
          <div>&nbsp;</div>
          <span>
            Sheep's Clothing
          </span>
        </section>
        <section>
          <h1>Dalu</h1>
          <h2>(Near-Human)</h2>
          <div>
            <label>Strength:</label>
            <span>{{ data.sheet.strength + 1 }}</span>
          </div>
          <div>
            <label>Dexterity:</label>
            <span>{{ data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Stamina:</label>
            <span>{{ data.sheet.stamina + 1 }}</span>
          </div>
          <div>
            <label>Manipulation:</label>
            <span>{{ data.sheet.manipulation - 1 }}</span>
          </div>
          <div>&nbsp;</div>
          <div>
            <label>Size:</label>
            <span>{{ parseInt(data.sheet.size) + 1 }}</span>
          </div>
          <div>
            <label>Defense:</label>
            <span>{{ data.sheet.wits > data.sheet.dexterity ? data.sheet.dexterity : data.sheet.wits }}</span>
          </div>
          <div>
            <label>Initiative:</label>
            <span>{{ data.sheet.wits + data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Speed:</label>
            <span>{{ parseInt(data.sheet.size) + 1 + data.sheet.strength + 1 + data.sheet.dexterity }}</span>
          </div>
          <div>
            <label>Perception:</label>
            <span>+1</span>
          </div>
          <div>&nbsp;</div>
          <span>
            Teeth and Claws &mdash; 0(L)<br />
            Defense vs. Firearms<br />
            Mild Lunacy
          </span>
        </section>
        <section>
          <h1>Gauru</h1>
          <h2>(Wolf-man)</h2>
          <div>
            <label>Strength:</label>
            <span>{{ data.sheet.strength + 3 }}</span>
          </div>
          <div>
            <label>Dexterity:</label>
            <span>{{ data.sheet.dexterity + 1 }}</span>
          </div>
          <div>
            <label>Stamina:</label>
            <span>{{ data.sheet.stamina + 2 }}</span>
          </div>
          <div>
            <label>Manipulation:</label>
            <span>{{ data.sheet.manipulation }}</span>
          </div>
          <div>&nbsp;</div>
          <div>
            <label>Size:</label>
            <span>{{ parseInt(data.sheet.size) + 2 }}</span>
          </div>
          <div>
            <label>Defense:</label>
            <span>{{ data.sheet.wits > (data.sheet.dexterity + 1) ? (data.sheet.dexterity + 1) : data.sheet.wits }}</span>
          </div>
          <div>
            <label>Initiative:</label>
            <span>{{ data.sheet.wits + data.sheet.dexterity + 1 }}</span>
          </div>
          <div>
            <label>Speed:</label>
            <span>{{ parseInt(data.sheet.size) + 2 + data.sheet.strength + 3 + data.sheet.dexterity + 1 }}</span>
          </div>
          <div>
            <label>Perception:</label>
            <span>+3</span>
          </div>
          <div>
            <label>Kuruth Limit:</label>
            <span>{{ data.sheet.stamina + data.sheet.primal_urge }}</span>
          </div>
          <div>&nbsp;</div>
          <span>
            Teeth and Claws &mdash; 2(L)<br />
            Defense vs. Firearms<br />
            Full Lunacy<br />
            Regeneration<br />
            Rage<br />
            Primal Fear
          </span>
        </section>
        <section>
          <h1>Urshul</h1>
          <h2>(Near-Wolf)</h2>
          <div>
            <label>Strength:</label>
            <span>{{ data.sheet.strength + 2 }}</span>
          </div>
          <div>
            <label>Dexterity:</label>
            <span>{{ data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Stamina:</label>
            <span>{{ data.sheet.stamina + 2 }}</span>
          </div>
          <div>
            <label>Manipulation:</label>
            <span>{{ data.sheet.manipulation - 1 }}</span>
          </div>
          <div>&nbsp;</div>
          <div>
            <label>Size:</label>
            <span>{{ parseInt(data.sheet.size) + 1 }}</span>
          </div>
          <div>
            <label>Defense:</label>
            <span>{{ data.sheet.wits > (data.sheet.dexterity + 2) ? (data.sheet.dexterity + 2) : data.sheet.wits }}</span>
          </div>
          <div>
            <label>Initiative:</label>
            <span>{{ data.sheet.wits + data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Speed:</label>
            <span>{{ parseInt(data.sheet.size) + 1 + data.sheet.strength + 2 + data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Perception:</label>
            <span>+3</span>
          </div>
          <div>&nbsp;</div>
          <span>
            Teeth 2(L) and Claws 1(L)<br />
            Defense vs. Firearms<br />
            Moderate Lunacy<br />
            Weaken the Prey
          </span>
        </section>
        <section>
          <h1>Urhan</h1>
          <h2>(Wolf)</h2>
          <div>
            <label>Strength:</label>
            <span>{{ data.sheet.strength }}</span>
          </div>
          <div>
            <label>Dexterity:</label>
            <span>{{ data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Stamina:</label>
            <span>{{ data.sheet.stamina + 1 }}</span>
          </div>
          <div>
            <label>Manipulation:</label>
            <span>{{ data.sheet.manipulation - 1 }}</span>
          </div>
          <div>&nbsp;</div>
          <div>
            <label>Size:</label>
            <span>{{ data.sheet.size - 1 }}</span>
          </div>
          <div>
            <label>Defense:</label>
            <span>{{ data.sheet.wits > (data.sheet.dexterity + 2) ? (data.sheet.dexterity + 2) : data.sheet.wits }}</span>
          </div>
          <div>
            <label>Initiative:</label>
            <span>{{ data.sheet.wits + data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Speed:</label>
            <span>{{ data.sheet.size - 1 + data.sheet.strength + data.sheet.dexterity + 2 }}</span>
          </div>
          <div>
            <label>Perception:</label>
            <span>+4</span>
          </div>
          <div>&nbsp;</div>
          <span>
            Teeth 1(L)<br />
            Chase Down
          </span>
        </section>
      </fieldset>
      <section class="other-traits">
        <header>Other Traits</header>
        <fieldset>
          <h1>Flesh Touchstone</h1>
          <textarea v-model.trim.lazy="data.sheet.touchstones.flesh"></textarea>
          <h1>Spirit Touchstone</h1>
          <textarea v-model.trim.lazy="data.sheet.touchstones.spirit"></textarea>
          <h1>Kuruth Triggers</h1>
          <textarea v-model.trim.lazy="data.sheet.kuruth_triggers"></textarea>
          <h1>Conditions</h1>
          <textarea v-model.trim.lazy="data.sheet.conditions"></textarea>
        </fieldset>
      </section>
      <fieldset class="gifts-and-rites">
        <header>
          Gifts and Rites
        </header>

        <section class="moon-gifts">
          <h1>Moon Gifts</h1>

          <div class="gift-list">
            <div v-for="gift of data.sheet.gifts.moon">
              <input type="text" v-model.trim.lazy="gift.list" />
              <DotGroup min="0" max="5" v-bind:value="gift.dots"
                v-on:dots="gift.dots = $event"></DotGroup>
            </div>
          </div>
        </section>
        <section class="shadow-gifts">
          <h1>Shadow Gifts</h1>

          <div class="gift-list-wrapper">
            <div class="gift-list">
              <div class="gift" v-for="(_, idx) of data.sheet.gifts.shadow" v-bind:key="idx">
                <input type="text" v-model.lazy="data.sheet.gifts.shadow[idx]" />
                <i class="far fa-minus-square" @click="data.sheet.gifts.shadow.splice(idx, 1)"></i>
              </div>
            </div>
          </div>
          <div class="control">
            <span title="add a shadow gift" @click="data.sheet.gifts.shadow.push('')"><i class="far fa-plus-square"></i>add a shadow gift</span>
          </div>
        </section>
        <section class="wolf-gifts">
          <h1>Wolf Gifts</h1>

          <div class="gift-list-wrapper">
            <div class="gift-list">
              <div class="gift" v-for="(_, idx) of data.sheet.gifts.wolf" v-bind:key="idx">
                <input type="text" v-model.trim.lazy="data.sheet.gifts.wolf[idx]" />
                <i class="far fa-minus-square" @click="data.sheet.gifts.wolf.splice(idx, 1)"></i>
              </div>
            </div>
          </div>
          <div class="control">
            <span title="add a wolf gift" @click="data.sheet.gifts.wolf.push('')"><i class="far fa-plus-square"></i>add a wolf gift</span>
          </div>
        </section>
        <section class="rites">
          <h1>Rites</h1>

          <div class="gift-list-wrapper">
            <div class="gift-list">
              <div class="gift" v-for="(_, idx) of data.sheet.rites" v-bind:key="idx">
                <input type="text" v-model.trim.lazy="data.sheet.rites[idx]" />
                <i class="far fa-minus-square" @click="data.sheet.rites.splice(idx, 1)"></i>
              </div>
            </div>
          </div>
          <div class="control">
            <span title="add a rite" @click="data.sheet.rites.push('')"><i class="far fa-plus-square"></i>add a rite</span>
          </div>
        </section>
      </fieldset>
    </article>
    <article id="page-3" class="page">
      <header>
        <img src="@/assets/CofD/WtF2e.png" />
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
  import Roll from "./CofD/Roll";
  import Skills from "./CofD/Skills";
  import TOC from "./TOC";

  export default {
  name: "WtF2e",
  props: ['data'],
  data() {
    return {
      locks: {
        harmony: true,
        primalUrge: true,
        renown: true
      }
    };
  },
  components: {
    Aspirations,
    Attributes,
    DotGroup,
    Health,
    Merits,
    Notes,
    Roll,
    Skills,
    TOC
  }
};
</script>

<style lang="scss">
@import "sass/basecofd";
@import "sass/wtf2e";
@import "../../assets/fonts/wtf2e.css";
</style>
