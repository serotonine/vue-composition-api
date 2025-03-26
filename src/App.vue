<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h2>{{ name }}</h2>
    <h3>{{ user.age  }}</h3>
  </section>
</template>

<script>
// Could also use <script setup>.
// No need to use setup() && export default.
//import { ref } from 'vue';
import { ref, reactive, isRef, isReactive, toRefs } from 'vue';

export default {
  setup() {
    // ref() return an object.
    // Let's create an object instead.
    const _user = reactive({
      name: 'Maximilien',
      age: 31,
    });
    const userRefs = toRefs(_user);
    const myRef = ref({
      name: 'Maximilien',
      age: 31,
    });
    console.log('_user', isReactive(_user));
    console.log('myRef', isRef(myRef));
    // Reactive is like ref but is only specially for object.
    // Skip value.
    setTimeout(() =>_user.name = 'Robert', 2000);
    return {
      user: _user,
      name: userRefs.name
    };
  },
  //   data() {
  //     return {
  //       userName: 'Maximilian',
  //     };
  //   },
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
