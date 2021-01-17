<template>

  <div id="app">
    
    <p>Your email is: {{email}}</p>

    <input v-model="email" class="input" :class="[email.length < 3 ? 'red' : 'green']">
    
    <button on-click="alert('Signed up')" :disabled="email.length < 3">
      Submit
    </button>

    <div id="app2">

      <input v-model="newCat" v-on:keyup.enter="addKitty">

      <button v-on:click="addKitty">+ ADD</button>

      <ul>
        <h3>Array</h3>
        <li v-for="cat in cats" :key="cat">{{cat}}</li>
      </ul>

      
      <ul>
        <h3>Object</h3>
        <li v-for="cat in cats2" :key="cat">{{cat.name}}</li>
      </ul>

    </div>

  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    
  },
  data () {
    return {
      email: 'cats@cats.com',
      cats: [
        'kitkat',
        'fish',
        'henry'
      ],
      cats2: [
        {name: 'kitkat'},
        {name: 'fish'},
        {name: 'henry'}
      ],
      newCat: ''
    }
  },
  methods: {
    addKitty: function() {
      this.cats.push(this.newCat), this.cats2.push({name: this.newCat});
      this.newCat = '';
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

#app2 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

.red {
  border: 6px solid red;
  outline: none;
}

.input {
  padding: 10px 10px;
  font-size: 20px;
}                 

.green {
  border: 6px solid green;
  outline: none;
}
</style>
