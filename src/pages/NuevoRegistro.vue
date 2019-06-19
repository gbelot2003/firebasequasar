<template>
  <div class="q-pa-md">
    <div class="column">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-md"
      >
        <q-input
          v-model="name"
          label="Your name *"
          hint="Name and surname"
        />

        <q-input
          type="number"
          v-model="age"
          label="Your age *"
        />
        <div>
          <q-btn label="Submit" type="submit" color="primary"/>
          <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm"/>
        </div>
      </q-form>
    </div>

  </div>
</template>

<script>
  import { QForm, QInput } from 'quasar';

    export default {
      name: 'NuevoRegistro',
      components: { QForm, QInput },
      data() {
        return {
          name: null,
          age: null,
        };
      },
      methods: {
        onSubmit() { },

        onReset() {
          this.name = null;
          this.age = null;
        },
      },
    };
</script>

<style scoped>

</style>
