<template>
  <q-page class="flex flex-center">

      <div class="col-4">
        Ratio: 1
    <q-img
          src="https://www.veleri.hr/studisweb/images/veleri_back.png"
          :ratio="1"
    />
  </div>
  <div class="q-pa-lg flex flex-center">
    <q-pagination
      v-model="current"
      :max="5"
      :input="true"
    >
    </q-pagination>
  </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  created () {
    // this.$axios.get('http://193.198.97.14:8000/api/biljnevrste/1/')
    //   .then(response => {
    //    this.posts = response.data.data.children
  // console.log(response)
    // })
    //  .catch(error => {
    //    console.log(error)
    //  })
  },

  methods: {
    loadData () {
      this.$axios.get('http://193.198.97.14:8000/api/biljnevrste/1/')
        .then((response) => {
          this.data = response.data
        })
        .catch(() => {
          this.$q.notify({
            color: 'negative',
            position: 'top',
            message: 'Loading failed',
            icon: 'report_problem'
          })
        })
    },

    data () {
      return {
        posts: [],
        current: 3
      }
    }

  // data () {
  //  return {
  //    current: 3
  //   }
  // }
  }
}
</script>
