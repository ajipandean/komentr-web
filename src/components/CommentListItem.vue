<template lang="html">
  <q-item class="q-px-none">
    <q-item-section
      top
      avatar
    >
      <q-avatar
        color="accent"
        text-color="white"
      >M</q-avatar>
    </q-item-section>
    <q-item-section>
      <q-item-label class="text-subtitle1 text-weight-medium q-mb-xs">
        mariobrows
      </q-item-label>
      <p class="no-margin text-grey-8">
        wkwkwkwk biasa ajasih sebenenrnya anime ini coba aja bayangkan mariobrows...
        <br>
        Ketidak jelasan
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
  data () {
    return {
      isInputShown: false
    }
  }
}
</script>
