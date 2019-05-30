<template>
  <div>
    <h1>猫の里親募集中リスト</h1>
    <b-table striped hover :items="cats">
      <template slot="name" slot-scope="data">
        <router-link :to="`/pets/cats/${data.index}`">
          {{ data.value }}
        </router-link>
      </template>
    </b-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {

  data() {
    return {}
  },
  computed: {
    ...mapState([
      'cats'
    ])
  }
  }
</script>
