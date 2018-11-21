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
    <article id="page-1" class="page cofd2e">
        <header>
            <img src="@/assets/CofD/CofD2e.png" />
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
                    <label for="vice">Vice:</label>
                    <input type="text" id="vice" name="vice" />
                </div>
                <div>
                    <label for="virtue">Virtue:</label>
                    <input type="text" id="virtue" name="virtue" />
                </div>
                <div>
                    <label for="concept">Concept:</label>
                    <input type="text" id="concept" name="concept" />
                </div>
            </section>
            <section class="right">
                <div>
                    <label for="faction">Faction:</label>
                    <input type="text" id="faction" name="faction" />
                </div>
                <div>
                    <label for="group">Group Name:</label>
                    <input type="text" id="group" name="group" />
                </div>
            </section>
        </fieldset>
    </article>
</template>

<script>
export default {
  name: 'CofD2e',
  props: ['data']
}
</script>

<style lang="scss">
@import "sass/cofd";

$blue: blue;

.page.cofd2e {
  &:before {
    background-image: url("../../assets/CofD/mortal-skull.png");
    background-position: center center;
    background-size: 250px;
    background-repeat: no-repeat;
    opacity: 0.4;
  }
}
</style>
