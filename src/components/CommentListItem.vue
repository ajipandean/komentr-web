<template lang="html">
  <q-item class="q-px-none">
    <q-item-section
      top
      side
    >
      <q-avatar
        size="32px"
        color="secondary"
        text-color="white"
        class="text-uppercase"
      >{{ comment.user.email.charAt(0) }}</q-avatar>
    </q-item-section>
    <q-item-section>
      <q-item-label class="text-subtitle1 text-weight-medium q-mb-sm">
        {{ comment.user.email }}
      </q-item-label>
      <p class="no-margin text-grey-8">
        {{ comment.message }}
      </p>
      <div class="q-mt-sm">
        <q-btn
          flat
          dense
          color="grey-8"
          label="reply"
          @click="isInputShown = !isInputShown"
        />
      </div>
      <comment-input v-if="isInputShown" />
    </q-item-section>
  </q-item>
</template>

<script type="text/javascript">
export default {
  components: {
    CommentInput: () => import('components/CommentInput.vue')
  },
  props: {
    comment: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      isInputShown: false
    }
  }
}
</script>
