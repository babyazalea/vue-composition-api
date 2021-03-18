<template>
  <section class="container">
    <user-data class="test" :first-name="firstName" :last-name="lastName" />
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First name" v-model="firstName" />
      <input type="text" placeholder="Last name" ref="lastNameInput" />
      <button @click="setLastName">Set Name</button>
    </div>
  </section>
</template>

<script>
import { ref, computed, watch, provide } from 'vue';
// import { reactive } from 'vue';
import UserData from './components/UserData.vue';

export default {
  components: { UserData },
  setup() {
    // const uName = ref('babyazalea');
    const uAge = ref(30);
    const firstName = ref('');
    const lastName = ref('');
    const lastNameInput = ref(null);
    // const user = reactive({
    //   name: 'babyazalea',
    //   age: 31
    // });

    provide('userAge', uAge);

    const uName = computed(function() {
      return firstName.value + ' ' + lastName.value;
    }); // computed, READONLY!!!!

    watch([uAge, uName], function(newValues, oldValues) {
      console.log('Old age: ' + oldValues[0]);
      console.log('New age: ' + newValues[0]);
      console.log('Old age: ' + oldValues[1]);
      console.log('New age: ' + newValues[1]);
    });

    function setNewAge() {
      uAge.value = 100;
    }

    function setLastName() {
      lastName.value = lastNameInput.value.value;
    }

    return {
      // user: user,
      setAge: setNewAge,
      userName: uName,
      age: uAge,
      firstName,
      lastName,
      lastNameInput,
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
