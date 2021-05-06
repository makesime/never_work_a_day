<template>
  <div class="moment">
    <v-card
      class="mx-auto my-12"
      max-width="690px"
    >
      <v-row>
        <v-list-item three-line>
          <v-list-item-avatar
            tile
            size="40"
          >
            <img
              :src="moment.user.avatar.thumb"
              :alt="moment.user.full_name"
            >
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-action-text class="moment-title">
              {{ moment.description }}
            </v-list-item-action-text>

            <v-list-item-subtitle class="moment-author">
              {{ momentAuthorWithTime }}
            </v-list-item-subtitle>
          </v-list-item-content>

          <influencer-toolbar
            :likes="moment.emotions.love"
            :comments_count="moment.comments_count"
            :attendance="moment.emotions.attendance"
           />
        </v-list-item>
      </v-row>
      <v-row>
        <v-img
          contain
          :lazy-src="moment.media.teaser"
          :src="moment.media.xlarge"
          height="690px"
        >
        </v-img>
      </v-row>
    </v-card>
  </div>
</template>

<script>
import moment from 'moment'
import InfluencerToolbar from '../components/InfluencerToolbar.vue'

export default {
  name: 'Moment',
  components: {
    InfluencerToolbar,
  },
  props: {
    moment: {
      type: Object
    }
  },
  computed: {
    momentAuthorWithTime: function() {
      const timeAgo = moment(this.moment.created_at).fromNow();
      return "by " + this.moment.user.full_name + " " + timeAgo;
    }
  }
}
</script>

<style lang="scss">
.moment {
  font-family: 'Lato', sans-serif;

  .moment-title {
    font-size: 16px;
    color: #444;
  }

  .moment-author {
    font-size: 13px;
    color: #ccc;
  }
}
</style>