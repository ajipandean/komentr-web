<template lang="html">
  <div class="q-my-sm">
    <q-input
      autogrow
      label="Write your comment..."
      v-model="comment"
    >
      <template v-slot:prepend>
        <q-btn
          flat
          dense
          round
          icon="emoji_emotions"
        />
      </template>
      <template v-slot:append>
        <q-btn
          flat
          dense
          round
          icon="photo"
        />
      </template>
      <template v-slot:after>
        <q-btn
          flat
          dense
          round
          color="primary"
          icon="send"
          :loading="isLoading"
          @click="handleSubmit"
        />
      </template>
    </q-input>
  </div>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      comment: '',
      isLoading: false
    }
  },
  methods: {
    async handleSubmit () {
      this.isLoading = true
      try {
        const token = this.$q.localStorage.getItem('token')
        await this.$axios({
          method: 'POST',
          url: 'http://localhost:8000/v1/secure/comments',
          headers: {
            Authorization: `Bearer ${token}`
          },
          data: {
            message: this.comment
          }
        })
      } catch (e) {
        console.error(e)
      } finally {
        this.isLoading = false
      }
    }
  }
}
</script>
