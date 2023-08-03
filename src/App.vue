<template>
  <div class="container text-center ">
    <div class="row mt-5">
      <div class="col-md-6 offset-md-3 border border-secondary-subtle">
        <TareaApp />
      </div>
    </div>
  </div>
  </template>
  <script>
    import TareaApp from './components/TareaApp.vue'

      /* eslint-disable */
      export default {
        components: { TareaApp },
        name: 'App',

      }
  </script>
