<template>
  <v-card-actions class="influencer-toolbar">
    <div class="influencer-icon">
      <v-btn
        small
        icon
        v-on:click="handleLikes"
      >
        <v-icon
          small
          :color="isLiked ? 'pink' : ''"
        >mdi-heart</v-icon>
      </v-btn>
      <span>{{ totalLikes }}</span>
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
  data() {
    return {
      isLiked: false,
      totalLikes : this.likes
    }
  },
  computed: {
  },
  methods: {
    handleLikes: function () {
      this.isLiked = !this.isLiked;
      this.isLiked ? this.totalLikes += 1 : this.totalLikes -= 1
    }
  }
}
</script>

<style lang="scss">
.influencer-toolbar {
  margin-bottom: 34px;
  padding: 10px 0 15px 20px;
  font-size: 13px;
}
</style>