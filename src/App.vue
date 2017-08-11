<template>
  <div :title="hi">
    <p v-text="hello"></p>
    <p v-html="hello"></p>
    {{ status ? 'success' : 'fail' }}
    <componentA>
      <p>123</p>
    </componentA>
    <ul>
      <li v-for="item in list"> {{ item.name + '-' + item.price }} </li>
    </ul>
        <a v-if="isPartA">partA</a>
        <a v-else>no data</a>
    <button @click="toggle">toggle</button>
    <button @click="addItem">addItem</button>
    <input v-model="myValue">
      {{ myValueWithoutNum }}
      <select v-model="selection">
          <option v-for="item in selectOption" :value="item.value">{{ item.text }}</option>
      </select>
      {{ selection }}
        <!--动画部分-->
      <button @click="toggleCom">fade toggle</button>
      <transition name="fade" mode="out-in">
        <div :is="currentView"></div>
      </transition>
  </div>
</template>

<script>
//  import Vue from 'vue'
import comA from './components/Hello.vue'
import comB from './components/Hi.vue'
export default {
  components: {
    comA, comB
  },
  computed: {
    myValueWithoutNum () {
      return this.myValue.replace(/\d/g, '')
    }
  },
  data () {
    return {
      show: true,
      currentView: 'com-a',
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
    },
    toggleCom () {
      if (this.currentView === 'com-a') {
        this.currentView = 'com-b'
      } else {
        this.currentView = 'com-a'
      }
    }
  }
}
</script>

<style>
html {
    height: 100%;
}

.fade-enter-active, .fade-leave-active {
    transition: opacity .5s ease-out;
}

.fade-enter, .fade-leave-active {
    opacity: 0;
}
</style>
