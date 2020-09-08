<template lang="html">
  <div v-if="!visible">
    <q-list>
      <q-item-label
        header
        class="q-px-none"
      >23 comments</q-item-label>
      <comment-list-item
        :key="i"
        :comment="comment"
        v-for="(comment, i) in comments"
      />
    </q-list>
  </div>
</template>

<script>
export default {
  components: {
    CommentListItem: () => import('components/CommentListItem.vue')
  },
  data () {
    return {
      visible: false,
      comments: []
    }
  },
  methods: {
    async handleFetch () {
      this.visible = true
      try {
        const { data } = await this.$axios.get('http://localhost:8000/v1/comments')
        this.comments = data
      } catch (e) {
        console.error(e)
      } finally {
        this.visible = false
      }
    }
  },
  created () {
    this.handleFetch()
  }
}
</script>
