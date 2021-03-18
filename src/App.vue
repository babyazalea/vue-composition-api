<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First name" @input="setFirstName" />
      <input type="text" placeholder="Last name" @input="setLastName" />
    </div>
  </section>
</template>

<script>
import { ref, computed } from 'vue';
// import { reactive } from 'vue';

export default {
  setup() {
    // const uName = ref('babyazalea');
    const uAge = ref(30);
    const firstName = ref('');
    const lastName = ref('');
    // const user = reactive({
    //   name: 'babyazalea',
    //   age: 31
    // });

    const uName = computed(function() {
      return firstName.value + ' ' + lastName.value;
    }); // computed, READONLY!!!!

    function setNewAge() {
      uAge.value = 100;
    }

    function setFirstName(event) {
      firstName.value = event.target.value;
    }

    function setLastName(event) {
      lastName.value = event.target.value;
    }

    return {
      // user: user,
      setAge: setNewAge,
      userName: uName,
      age: uAge.value,
      setFirstName,
      setLastName
    };
  }
  // data() {
  //   return {
  //     userName: 'babyazalea',
  //     age: 31
  //   };
  // },
  // methods: {
  //   setNewAge() {
  //     this.age = 32;
  //   }
  // }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
