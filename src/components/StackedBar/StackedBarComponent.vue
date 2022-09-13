<template>
    <div v-if="data.length !== 0" id="stackedBar">
      <ul class="legend__stack">
        <li
          v-show="object.value !== 0"
          v-for="(object, number) in data"
          :key="object.id"
          class="series__legend"
          ref="legend"
          @click="selected(object)"
        >
          <i :style="bgColor(object) + txtColor(object)" class="marker__legend" />
          <span class="text__legend">
            {{ object.title }}
          </span>
        </li>
      </ul>
      <div class="wrap__stack">
        <div
          v-show="item.value !== 0"
          class="item__stack"
          v-for="(item, index) in data"
          :key="index"
          ref="stack"
          :style="bgColor(item) + 'flex-basis:' + item.percent + '%;'"
        >
          <!-- <div class="percent__stack">
            <span class="text__stack">
              <strong>{{ Math.round(item.percent) }}%</strong>
            </span>
          </div> -->
          <div class="label__stack">
            <span class="text__stack">
              <strong>{{ item.value }}</strong>
            </span>
          </div>
        </div>
      </div>
    </div>
    <div v-else class="wrap__stack data-not-found">
      <span>Data is Not Found!</span>
    </div>
  </template>
    
  <script >
  export default {
    name: "StackedProgressBar",
    props: {
      data: {
        type: Array,
        default: null,
      },
    },
    data() {
      return {
        colors: [
          "#007bff",
          "#6610f2",
          "#6f42c1",
          "#e83e8c",
          "#dc3545",
          "#fd7e14",
          "#ffc107",
          "#28a745",
          "#20c997",
          "#17a2b8",
          "#516f7d",
          "#343a40",
          "#ff5a46",
          "#989486",
          "#f28b8c",
        ],
      };
    },
    methods: {
      bgColor(item) {
        if (item.color) {
          return `background-color:` + item.color + `;`;
        }
        const randomChoice = this.colors[
          Math.floor(Math.random() * this.colors.length)
        ];
        return `background-color:${randomChoice};`;
      },
      txtColor(item) {
        if (item.color) {
          return `color:` + item.color + `;`;
        }
        const randomChoice = this.colors[
          Math.floor(Math.random() * this.colors.length)
        ];
        return `color:${randomChoice};`;
      },
      selected(item){
        console.log(item)
      }
    },
  };
  </script>
  <style scoped>
    @charset "utf-8";

#stackedBar {
  display: flex;
  flex-direction: column-reverse;
}

.wrap__stack {
  display: flex;
  border: none;
  background-color: #ffffff;
}

.item__stack {
  position: relative;
}

.item__stack:hover,
.item__stack:focus,
.item__stack.item-active,
.series__legend.item-active {
  box-shadow: inset 200px 200px 0px 200px inherit;
  opacity: 0.85;
}

.item__stack.item-disabled,
.series__legend.item-disabled,
.wrap__stack:hover .item__stack:not(:hover) {
  opacity: 0.2;
}

.label__stack,


.label__stack {
  font-weight: 600;
  background-color: rgba(0, 0, 0, 0);
  border-color: rgba(0, 0, 0, 0);
}

.percent__stack {
  position: static;
  display: block;
  min-width: 3rem;
  max-width: 3rem;
  margin: .25rem auto;
  font-weight: 600;
  background-color: rgba(0, 0, 0, 0);
  border-color: rgba(0, 0, 0, 0);
  opacity: 1;
}

.item__stack:hover .label__stack {
  opacity: 1;
}

.item__stack:hover .percent__stack {
  opacity: 0;
}

.legend__stack {
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: auto;
  margin-top: 1rem;
  padding: 0 1rem;
}

.series__legend {
  display: block;
  width: auto;
  margin: 0 .5rem;
  align-items: center;
  cursor: pointer;
  line-height: normal;
}

.marker__legend {
  position: relative;
  left: 0;
  right: 0;
  top: 0;
  display: inline-block;
  width: 12px;
  height: 12px;
  margin-right: 0.3rem;
  border-width: 0;
  border-color: #fff;
  border-radius: 2px;
  cursor: pointer;
  vertical-align: middle;
}

.text__legend {
  position: relative;
  font-size: .750rem;
  color: #333333;
}

  </style>
  