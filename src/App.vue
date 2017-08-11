<template>
  <div :title="hi">
    <p v-text="hello"></p>
    <p v-html="hello"></p>
    {{ status ? 'success' : 'fail' }}
    <componentA></componentA>
    <ul>
      <li v-for="(value, key) in objList"> {{ key + '-' + value }} </li>
    </ul>
  </div>
</template>

<script>
import componentA from './components/Hello.vue'
export default {
  components: {
    componentA: componentA
  },
  data () {
    return {
      hello: '<span>world</span>',
      hi: 'hi',
      num: 1,
      status: false,
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
  }
}
</script>

<style>
html {
    height: 100%;
}
</style>
