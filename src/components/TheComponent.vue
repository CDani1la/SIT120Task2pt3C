<template>
    <div>
      <h2>{{ title }}</h2>
      <slot>This is a Component from MyComponent vue</slot>
      <button @click="emitEvent">Click mHere</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
    },
    methods: {
      emitEvent() {
        this.$emit('custom-event', 'Event message from child component');
        console.log('custom-event', 'Event message from component');
      },
    },
  };
  </script>