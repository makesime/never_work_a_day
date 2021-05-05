<template>
  <div class="momentList" v-if="moments">
    <div
      v-for="moment in moments"
      :key="moment.id">
        <moment :moment="moment" />
    </div>
  </div>
</template>

<script>
import Moment from '../components/Moment.vue'

const axios = require('axios');

export default {
  name: 'MomentList',
  components: {
    Moment
  },
  data() {
    return {
      moments: null,
    }
  },
  created: function(){
    this.fetchMoments();
  },
  methods: {
    fetchMoments: function() {
      var self = this;

      axios.get('/organizations/mirego/moments')
      .then(function (response) {
        self.moments = response.data;
      })
      .catch(function (error) {
        console.log(error);
      });
    }
  }
}
</script>

<style>

</style>