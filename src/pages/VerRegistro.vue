<template>
    <h5>{{ name }}</h5>
</template>

<script>
    import db from '../conf/firebaseInit';

    export default {
        name: 'VerRegistro',
        data() {
          return {
            employee_id: null,
            name: null,
            dept: null,
            position: null,
          };
        },
        created() {
          console.log(this.$route.params);
          this.ferchData();
        },
        methods: {
          ferchData() {
            db.collection('employees')
              .where('employee_id', '==', this.$route.params.id).get()
              .then((rest) => {
                rest.forEach((doc) => {
                  console.log(doc.data());
                  this.employee_id = doc.data().employee_id;
                  this.name = doc.data().name;
                  this.dept = doc.data().dept;
                  this.position = doc.data().position;
                });
              });
          },
        },
    };
</script>

<style scoped>

</style>
