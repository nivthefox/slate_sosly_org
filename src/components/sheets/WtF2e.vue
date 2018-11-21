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
    <form>
        <article id="page-1" class="page wtf2e">
            <header>
                <img src="@/assets/CofD/WtF2e.png" />
            </header>

            <fieldset class="personal-info">
                <section class="left">
                    <div>
                        <label for="name">Name:</label>
                        <input type="text" id="name" name="name" v-model="data.name" />
                    </div>
                    <div>
                        <label for="player">Player:</label>
                        <input type="text" id="player" name="player" v-model="data.userId" disabled />
                    </div>
                    <div>
                        <label for="chronicle">Chronicle:</label>
                        <input type="text" id="chronicle" name="chronicle" v-model="data.sheet.chronicle" />
                    </div>
                </section>
                <section class="middle">
                    <div>
                        <label for="blood">Blood:</label>
                        <input type="text" id="blood" name="blood" v-model="data.sheet.blood" />
                    </div>
                    <div>
                        <label for="bone">Bone:</label>
                        <input type="text" id="bone" name="bone" v-model="data.sheet.bone" />
                    </div>
                    <div>
                        <label for="concept">Concept:</label>
                        <input type="text" id="concept" name="concept" v-model="data.sheet.concept" />
                    </div>
                </section>
                <section class="right">
                    <div>
                        <label for="auspice">Auspice:</label>
                        <input type="text" id="auspice" name="auspice" v-model="data.sheet.auspice" />
                    </div>
                    <div>
                        <label for="tribe">Tribe:</label>
                        <input type="text" id="tribe" name="tribe" v-model="data.sheet.tribe" />
                    </div>
                    <div>
                        <label for="lodge">Lodge:</label>
                        <input type="text" id="lodge" name="lodge" v-model="data.sheet.lodge" />
                    </div>
                </section>
            </fieldset>
            <fieldset class="attriutes">
                <header>Attributes</header>
                <table>
                    <tr>
                        <th>Power</th>
                        <td>
                            <fieldset>
                                <label for="intelligence">Intelligence</label>
                                <!-- //-->
                                <DotGroup max="5" min="1" name="intelligence" v-bind:value="data.sheet.intelligence"></DotGroup>
                                <!-- //-->
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="strength">Strength</label>
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="presence">Presence</label>
                            </fieldset>
                        </td>
                    </tr>
                    <tr>
                        <th>Finesse</th>
                        <td>
                            <fieldset>
                                <label for="wits">Wits</label>
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="dexterity">Dexterity</label>
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="manipulation">Manipulation</label>
                            </fieldset>
                        </td>
                    </tr>
                    <tr>
                        <th>Resistance</th>
                        <td>
                            <fieldset>
                                <label for="resolve">Resolve</label>
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="stamina">Stamina</label>
                            </fieldset>
                        </td>
                        <td>
                            <fieldset>
                                <label for="composure">Composure</label>
                            </fieldset>
                        </td>
                    </tr>
                </table>
            </fieldset>
        </article>
    </form>
</template>

<script>
import DotGroup from "@/components/sheets/DotGroup";

export default {
  name: "WtF2e",
  props: ["data"],
  components: {
    DotGroup
  }
};
</script>

<style lang="scss">
@import "sass/cofd";
@import "../../assets/fonts/wtf2e.css";

$brown: saddlebrown;
$pencil: #333333;

.page.wtf2e {
  &:before {
    background-color: $brown;
    mask-image: url("../../assets/CofD/forsaken-skull.png");
    mask-position: center center;
    mask-repeat: no-repeat, no-repeat;
    -webkit-mask-image: url("../../assets/CofD/forsaken-skull.png");
    -webkit-mask-position: center center;
    -webkit-mask-repeat: no-repeat, no-repeat;
    opacity: 0.2;
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
}
</style>
