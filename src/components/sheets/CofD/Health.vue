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
    <section class="health-track">
      <i class="fas fa-plus" @click="showModal('healing')"></i>
      <span class="track">
        <span class="health-container" v-for="(_, i) of dots" v-bind:key="i" >
          <span class="box">
            <i class="fas fa-asterisk" v-if="isAggravated(i)"></i>
            <i class="fas fa-times" v-if="isLethal(i)"></i>
            <i class="fas fa-slash" v-if="isBashing(i)"></i>
          </span>
          <br v-if="i === 9" />
        </span>
      </span>
      <i class="fas fa-minus" @click="showModal('damage')"></i>
      <dialog id="damage">
        <label v-if="action === 'damage'">Damage</label>
        <label v-if="action === 'healing'">Healing</label>
        <fieldset>
          <input type="number" id="amount" min="0" v-bind:max="health.max" v-model.number="amount" />
          <select id="type" v-model="type">
            <option value="bashing" selected>Bashing</option>
            <option value="lethal">Lethal</option>
            <option value="aggravated">Aggravated</option>
          </select>
        </fieldset>
        <div class="actions">
          <i class="fas fa-check" @click="calculate()"></i>
          <i class="fas fa-ban" @click="hideModal()"></i>
        </div>
      </dialog>
    </section>
</template>

<script>
  export default {
    name: "Health",
    props: ["health"],
    data: function () {
      return {
        action: '',
        amount: 0,
        type: "bashing"
      }
    },
    computed: {
      dots: function () {
        const arr = [];
        for (let i = 0; i < this.health.max; i++) {
          arr.push(i);
        }
        return arr;
      },
      modal: function () {
        return document.getElementById('damage');
      }
    },
    methods: {
      isAggravated(i) {
        return i < this.health.aggravated;
      },
      isLethal(i) {
        const offset = this.health.aggravated;
        return i >= offset && (i - offset) < this.health.lethal;
      },
      isBashing(i) {
        const offset = this.health.aggravated + this.health.lethal;
        return i >= offset && (i - offset) < this.health.bashing;
      },
      hideModal() {
        this.amount = 0;
        this.type = 'bashing';

        this.modal.close();
      },
      showModal(action) {
        this.action = action;
        this.modal.showModal();
      },
      calculate() {
        console.log(this);
        const direction = this.action === 'damage' ? 1 : -1;

        switch (this.type) {
          case 'aggravated':
            this.health.aggravated += (direction * this.amount);
            break;
          case 'bashing':
            this.health.bashing += (direction * this.amount);
            break;
          case 'lethal':
            this.health.lethal += (direction * this.amount);
            break;
        }

        const damage = () => (this.health.aggravated + this.health.lethal + this.health.bashing);
        while (damage() > this.health.max) {
          if (this.health.bashing > 0) {
            this.health.bashing = Math.max(this.health.bashing - 2, 0);
            this.health.lethal++;
          }
          else if (this.health.lethal > 0) {
            this.health.lethal = Math.max(this.health.lethal - 2, 0);
            this.health.aggravated++;
          }
          else {
            // we can't roll agg over.
            return;
          }
        }

        this.hideModal();
      }
    }
  };
</script>

<style lang="scss">
  section.health-track {
    display: inline-block;
    margin-top: 5px;



    i.fas { cursor: pointer; }

    .track {
      display: inline-block;
      margin: 0 0.1in;
    }

    .box {
      border: 1px solid black;
      color: #333;
      display: inline-block;
      height: 13px;
      margin: 0 2px;
      width: 13px;
      vertical-align: top;

      .fas { vertical-align: top; }
      .fa-asterisk { font-size: 9pt; }
      .fa-times { font-size: 11pt; }
      .fa-slash { font-size: 9pt; }
    }

    dialog {
      padding: 0;

      label {
        background: #333;
        color: #FFF;
        display: block;
        font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
        font-size: 20pt;
        padding: 0.1in;
      }

      fieldset {
        padding: 0.2in;

        input[type=number], select {
          font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
          font-size: 14pt;
        }
        input[type=number] {
          border: 2px solid #333;
          border-radius: 4px;
          height: 40px;
          margin: 0;
          margin-right: 1em;
          padding: 0;
          text-align: center;
          width: 40px;
        }
      }

      .actions {
        padding: 0.1in;
        text-align: right;

        i {
          cursor: pointer;
          margin-left: 0.1in;

          &:hover {
            &.fa-check { color: limegreen; }
            &.fa-ban { color: red; }
          }
        }
      }
    }
  }
</style>
