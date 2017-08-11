<template>
  <div :title="hi">
    <p v-text="hello"></p>
    <p v-html="hello"></p>
    {{ status ? 'success' : 'fail' }}
    <componentA></componentA>
    <ul>
      <li v-for="item in list"> {{ item.name + '-' + item.price }} </li>
    </ul>
    <a v-if="isPartA">partA</a>
    <a v-else>no data</a>
    <button @click="toggle">toggle</button>
    <button @click="addItem">addItem</button>
    <input v-model.number="myValue">
      {{ myValue }}
      <select v-model="selection">
          <option v-for="item in selectOption" :value="item.value">{{ item.text }}</option>
      </select>
      {{ selection }}
  </div>
</template>

<script>
//  import Vue from 'vue'
import componentA from './components/Hello.vue'
export default {
  components: {
    componentA: componentA
  },
  data () {
    return {
      selectOption: [
        {
          text: 'apple',
          value: 0
        },
        {
          text: 'banana',
          value: 1
        }
      ],
      selection: null,
      myValue: '',
      hello: '<span>world</span>',
      hi: 'hi',
      num: 1,
      status: false,
      isPartA: true,
      list: [
        {
          name: 'apple',
          price: 34
        },
        {
          name: 'orgina',
          price: 12
        },
        {
          name: 'banana',
          price: 35
        }
      ],
      objList: {
        name: 'apple',
        price: 34,
        color: 'red',
        weight: 14
      }
    }
  },
  methods: {
    addItem () {
      this.list.push({
        name: 'qweqwe',
        price: 123
      })
    },
    toggle () {
      this.isPartA = !this.isPartA
    }
  }
}
</script>

<style>
html {
    height: 100%;
}
</style>
