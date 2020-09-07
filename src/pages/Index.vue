<template lang="html">
  <main-layout>
    <q-page class="q-pa-md">
      <loggedin-user />
      <comment-input />
      <comment-list />
    </q-page>
  </main-layout>
</template>

<script type="text/javascript">
export default {
  components: {
    MainLayout: () => import('layouts/Main.vue'),
    LoggedinUser: () => import('components/LoggedinUser.vue'),
    CommentInput: () => import('components/CommentInput.vue'),
    CommentList: () => import('components/CommentList.vue')
  }
}
</script>
