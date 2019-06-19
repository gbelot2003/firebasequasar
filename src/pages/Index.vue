<template>
  <div class="q-pa-md">
    <div class="column">
    <h4>Listado de Registros</h4>
      <q-list>
        <q-item clickable
                v-for="item in employees"
                v-bind:key="item.id"
                class="q-my-sm"
                tag="a"
                :href="renderMessage(item.employee_id)"
        >
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ item.name }}</q-item-label>
            <q-item-label caption>{{ item.position }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </div>

  </div>
</template>

<script>
  import {
    QList, QItem, QItemSection, QItemLabel,
  } from 'quasar';
  import db from '../conf/firebaseInit';


  export default {
    name: 'PageIndex',
    components: {
      QList, QItem, QItemSection, QItemLabel,
    },
    data() {
      return {
        employees: [],
      };
    },
    methods: {
      renderMessage(index) {
        return `#/ver/${index}`;
      },
    },
    created() {
      db.collection('employees').orderBy('dept').get().then((rest) => {
        rest.forEach((doc) => {
          const data = {
            id: doc.id,
            employee_id: doc.data().employee_id,
            name: doc.data().name,
            dept: doc.data().dept,
            position: doc.data().position,
          };
          this.employees.push(data);
        });
      });
    },
  };
</script>
