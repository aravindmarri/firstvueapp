<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <span v-text=" 'v-text :' +msg"></span>
    <div v-html=" 'v-html :' + htmlTemp"></div>
    <button @click="toggleBool()" type="button">Click here...</button>
    <p v-once>initial value : {{ testBool }}</p>
    <p  v-cloak>{{ testBool }}</p>
    <div v-show="testBool">Hello Vue Show</div>

    <div v-if="false">hello v-if</div>
    <p v-else>hello v-else</p>
    <p>v-for loop</p>
    <ul v-for="(item, index) in emp" :key="item.id">
      <li :id="index"> {{ item.name }} - {{ item.role }}</li>
    </ul>
    <div .="objectOfAttrs"> Today Date : {{ getDate() }}</div>

    <input v-model="message" placeholder="edit me"/>
    <p>
      v-model binding : {{ message }}
    </p>


  </div>
</template>

<script>
import {defineComponent, ref} from "vue";

export default defineComponent({
  props: {
    msg: String
  },
  setup() {
    const objectOfAttrs = {
      id: 'container',
      class: 'wrapper'
    }
    let testBool = ref(true)
    let inputText = "Enter Something"
    let message = ref("Enter Something")

    let emp = [
      {name: 'Malhar', role: 'Lead'},
      {name: 'Aravind', role: 'Web dev'},
      {name: 'Charan', role: 'Intern'}
    ]
    const htmlTemp = '<p>html content</p>'

    function getDate() {
      return new Date().toString();
    }

    function toggleBool() {
      testBool.value = !testBool.value;
    }

    return {toggleBool, getDate, htmlTemp, testBool, objectOfAttrs, emp, inputText, message}
  }
})

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

[v-cloak] {
  display: none;
}
</style>
