<template>
  <v-card-actions class="influencer-toolbar">
    <div class="influencer-icon">
      <v-btn small icon>
        <v-icon small>mdi-heart</v-icon>
      </v-btn>
      <span>{{ likes }}</span>
    </div>
    <div class="influencer-icon">
      <v-btn small icon>
        <v-icon small>mdi-account</v-icon>
      </v-btn>
      <span>{{ comments_count }}</span>
    </div>
    <div class="influencer-icon">
      <v-btn small icon>
        <v-icon small>mdi-comment</v-icon>
      </v-btn>
      <span>{{ attendance }}</span>
    </div>
  </v-card-actions>
</template>

<script>
export default {
  name: 'InfluencerToolbar',
  props: {
    likes: {
      type: Number,
      required: true
    },
    comments_count: {
      type: Number,
      required: true
    },
    attendance: {
      type: Number,
      required: true
    },
  },
}
</script>

<style lang="scss">
.influencer-toolbar {
  margin-bottom: 34px;
  padding: 10px 0 15px 20px;
  font-size: 13px;
}
</style>