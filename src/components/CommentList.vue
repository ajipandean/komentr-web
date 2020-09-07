<template lang="html">
  <div>
    <q-list>
      <q-item-label
        header
        class="q-px-none"
      >23 comments</q-item-label>
      <comment-list-item />
    </q-list>
  </div>
</template>

<script>
export default {
  components: {
    CommentListItem: () => import('components/CommentListItem.vue')
  }
}
</script>
