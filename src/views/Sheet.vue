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
    <CofD2e v-if="sheet.type === 'cofd2e'" v-bind:data="sheet"></CofD2e>
    <WtF2e v-if="sheet.type === 'wtf2e'" v-bind:data="sheet"></WtF2e>
  </div>
</template>

<script>
  import CofD2e from "@/components/sheets/CofD2e.vue";
  import WtF2e from "@/components/sheets/WtF2e.vue";

  export default {
    name: "sheet",
    data: function () {
      window.data = {
        sheet: {
          name: "Lachlan Morrison",
          type: "wtf2e",
          userId: "Vale#8130",
          sheet: {
            chronicle: "Beneath the Reek",
            blood: "The Fox",
            bone: "Wallflower",
            concept: "Wealthy Vagabond",
            auspice: "Irraka",
            tribe: "Hunters in Darkness",
            lodge: "",
            intelligence: 3,
            wits: 3,
            resolve: 2,
            strength: 2,
            dexterity: 3,
            stamina: 2,
            presence: 1,
            manipulation: 2,
            composure: 3,
            academics: {
              dots: 2
            },
            computer: {
              dots: 0
            },
            crafts: {
              dots: 0
            },
            investigation: {
              dots: 0
            },
            medicine: {
              dots: 1
            },
            occult: {
              dots: 0
            },
            politics: {
              dots: 1,
              specialties: 'Investments'
            },
            science: {
              dots: 0
            },
            athletics: {
              dots: 2,
              specialties: 'Parkour'
            },
            brawl: {
              dots: 1
            },
            drive: {
              dots: 0
            },
            firearms: {
              dots: 1
            },
            larceny: {
              dots: 0
            },
            stealth: {
              dots: 0
            },
            survival: {
              dots: 3,
              specialties: 'Hunting'
            },
            weaponry: {
              dots: 0
            },
            animal_ken: {
              dots: 3
            },
            empathy: {
              dots: 1
            },
            expression: {
              dots: 0
            },
            intimidation: {
              dots: 0
            },
            persuasion: {
              dots: 1
            },
            socialize: {
              dots: 3
            },
            streetwise: {
              dots: 3
            },
            subterfuge: {
              dots: 1
            },
            merits: [
              {
                name: "Multilingual (French, Scots-Gaelic)",
                dots: 1
              },
              {
                name: "Parkour",
                dots: 1
              },
              {
                name: "Resources",
                dots: 4
              },
              {
                name: "Trained Observer",
                dots: 1
              },
              {
                name: "True Friend (Bran)",
                dots: 3
              },
              { dots: 0 },
              { dots: 0 },
              { dots: 0 },
              { dots: 0 },
              { dots: 0 },
              { dots: 0 },
              { dots: 0 }
            ],
            primal_urge: 1,
            essence: {
              current: 10,
              max: 10
            },
            willpower: {
              current: 5,
              max: 5
            },
            harmony: 7,
            size: 5,
            health: {
              max: 7,
              aggravated: 2,
              lethal: 1,
              bashing: 2
            },
            renown: {
              cunning: 1,
              glory: 0,
              honor: 0,
              purity: 1,
              wisdom: 1
            },
            gifts: {
              moon: [
                {
                  name: "New Moon",
                  dots: 1
                }
              ],
              shadow: [
                {
                  name: "Hit and Run",
                  list: "Evasion"
                },
                {
                  name: "Running Silent",
                  list: "Stealth"
                }
              ],
              wolf: [
                {
                  name: "Skin Thief",
                  list: "Change"
                }
              ]
            },
            rites: ["Hunting Ground"],
            experiences: 1,
            beats: 1
          }
        }
      };
      return window.data;
    },
    components: {
      CofD2e,
      WtF2e
    }
  };
</script>
