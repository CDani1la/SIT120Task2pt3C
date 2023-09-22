<template>
    <div>
      <h3>{{ title }}</h3>
      <p>{{ content }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['title', 'content'],
  };
  </script>
  
  <style scoped>
  /* Scoped CSS styles for the component */
  h3 {
    color: blue;
  }
  </style>