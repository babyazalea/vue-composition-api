<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </section>
</template>

<script>
// import { ref } from 'vue';
// import {isReactive, isRef} from 'vue
import { reactive, toRefs } from 'vue';

export default {
  setup() {
    // const uName = ref('babyazalea');
    // const uAge = ref(30);
    const user = reactive({
      name: 'babyazalea',
      age: 31
    });

    // console.log(isRef(uAge));
    // console.log(isReactive(user), user.age);

    setTimeout(function() {
      // uName.value = 'ty';
      // uAge.value = 33;
      user.name = 'ty';
      user.age = 30;
    }, 2000);

    const userRefs = toRefs(user);

    return { user: user, userName: userRefs.name, age: userRefs.age };
  }
  // data() {
  //   return {
  //     userName: 'babyazalea',
  //   };
  // },
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
