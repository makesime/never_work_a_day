<template>
  <div class="moment-list">
    <div class="organization" v-if="organization">
      <v-avatar
        tile
        size="30"
      >
        <v-img
          :src="organization.avatar.thumb"
        />
      </v-avatar>
      <h1>{{ organization.name }}</h1>
      <h3>{{ organization.description }}</h3>
    </div>
    <div v-if="moments">
      <span
        v-for="moment in moments"
        :key="moment.id">
          <moment :moment="moment" />
      </span>
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
      organization: null,
    }
  },
  created() {
    this.fetchMoments();
    this.fetchOrganization();
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
    },
    fetchOrganization: function() {
      var self = this;

      axios.get('/organizations/mirego')
      .then(function (response) {
        self.organization = response.data;
      })
      .catch(function (error) {
        console.log(error);
      });
    }
  }
}
</script>

<style lang="scss">
.moment-list {
  .organization {
    text-align: center;
  }
}
</style>