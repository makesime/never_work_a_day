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
            <v-list-item-text class="moment-title">
              {{ moment.description }}
            </v-list-item-text>

            <v-list-item-subtitle class="moment-author">
              {{ momentAuthorWithTime }}
            </v-list-item-subtitle>
          </v-list-item-content>

          <v-card-actions>
            <div>
              <v-btn icon>
                <v-icon>mdi-heart</v-icon>
              </v-btn>
              <span>{{ moment.emotions.love }}</span>
            </div>
            <div>
              <v-btn icon>
                <v-icon>mdi-account</v-icon>
              </v-btn>
              <span>{{ moment.comments_count }}</span>
            </div>
            <div>
              <v-btn icon>
                <v-icon>mdi-comment</v-icon>
              </v-btn>
              <span>{{ moment.emotions.attendance }}</span>
            </div>
          </v-card-actions>
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

export default {
  name: 'Moment',
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