<template>
  <div class="moment-list">
    <div class="organization" v-if="organization">
      <v-avatar
        class="organization-avatar"
        tile
        size="30"
      >
        <v-img
          :src="organization.avatar.thumb"
        />
      </v-avatar>
      <div class="text-h3 title">{{ organization.name }}</div>
      <div class="text-subtitle-1 subtitle">{{ organization.description }}</div>
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
  font-family: 'Lato', sans-serif;

  .organization {
    text-align: center;
    padding-top: 70px;
    padding-bottom: 80px;

    .organization-avatar {
      margin-bottom: 15px;
    }

    .subtitle {
      padding: 15px 80px 0 80px;
      color: #a9b3bd;
    }

    .title {
      font-weight: 900;
    }
  }
}
</style>