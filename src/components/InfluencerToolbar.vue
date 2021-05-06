<template>
  <v-card-actions>
    <div>
      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>
      <span>{{ likes }}</span>
    </div>
    <div>
      <v-btn icon>
        <v-icon>mdi-account</v-icon>
      </v-btn>
      <span>{{ comments_count }}</span>
    </div>
    <div>
      <v-btn icon>
        <v-icon>mdi-comment</v-icon>
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

<style>

</style>