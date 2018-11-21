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
  name: 'sheet',
  data: function() {
    return {
      sheet: {
        name: 'Lachlan Morrison',
        type: 'wtf2e',
        userId: 'Vale#8130',
        sheet: {
          chronicle: 'Beneath the Reek',
          blood: 'The Fox',
          bone: 'Wallflower',
          concept: 'Wealthy Vagabond',
          auspice: 'Irraka',
          tribe: 'Hunters in Darkness',
          lodge: '',
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
          medicine: {
            dots: 1
          },
          politics: {
            dots: 1,
            specialties: ['Investments']
          },
          athletics: {
            dots: 2,
            specialties: ['Parkour']
          },
          brawl: {
            dots: 1
          },
          firearms: {
            dots: 1
          },
          survival: {
            dots: 3,
            specialties: ['Hunting']
          },
          animal_ken: {
            dots: 3
          },
          empathy: {
            dots: 1
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
              name: 'Multilingual',
              dots: 1,
              details: 'French, Scots-Gaelic'
            },
            {
              name: 'Parkour',
              dots: 1
            },
            {
              name: 'Resources',
              dots: 4
            },
            {
              name: 'Trained Observer',
              dots: 1
            },
            {
              name: 'True Friend',
              dots: 3,
              details: 'Bran'
            }
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
            aggravated: 0,
            lethal: 0,
            bashing: 0
          },
          renown: {
            cunning: 1,
            glory: 0,
            honor: 0,
            purity: 1,
            wisdom: 1
          },
          gifts: {
            moon: [{
              name: 'New Moon',
              dots: 1
            }],
            shadow: [
              {
                name: 'Hit and Run',
                list: 'Evasion'
              },
              {
                name: 'Running Silent',
                list: 'Stealth'
              }
            ],
            wolf: [
              {
                name: 'Skin Thief',
                list: 'Change'
              }
            ]
          },
          rites: ['Hunting Ground'],
          experiences: 1,
          beats: 1
        }
      }
    };
  },
  components: {
    CofD2e,
    WtF2e
  }
};
</script>
