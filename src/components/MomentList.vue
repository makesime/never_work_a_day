<template>
  <div class="momentList" v-if="moments">
    <div
      v-for="moment in moments"
      :key="moment.id">
        <h1>{{ moment }}</h1>
    </div>
  </div>
</template>

<script>
const axios = require('axios');

export default {
  name: 'MomentList',
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
      })
      .then(function () {
        // always executed
      });
    }
  }
}
</script>

<style>

</style>