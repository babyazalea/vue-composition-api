<template>
  <div>
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script>
import {
  computed,
  inject,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted
} from 'vue';

export default {
  props: ['firstName', 'lastName'],
  setup(props, context) {
    const uName = computed(function() {
      return props.firstName + ' ' + props.lastName;
    });

    const age = inject('userAge');

    console.log(context);
    // in context, attr, slot, emit
    // context.emit(); = this.$emit()

    onBeforeMount(function() {
      console.log('onBeforeMount');
    });

    onMounted(function() {
      console.log('onMounted');
    });

    onBeforeUpdate(function() {
      console.log('onBeforeUpdate');
    });

    onUpdated(function() {
      console.log('onUpdated');
    });

    onBeforeUnmount(function() {
      console.log('onBeforeUnmount');
    });

    onUnmounted(function() {
      console.log('onUnmounted');
    });

    return { userName: uName, age };
  }
  //   computed: {
  //     userName() {
  //       return this.firstName + ' ' + this.lastName;
  //     }
  //   }
};
</script>
