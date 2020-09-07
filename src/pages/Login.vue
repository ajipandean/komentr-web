<template lang="html">
  <div class="flex flex-center fullscreen">
    <q-card style="width:400px;max-width: 500px;">
      <q-card-section class="q-pb-none">
        <div class="text-h6">Welcome</div>
      </q-card-section>
      <q-form @submit.prevent="handleSubmit">
        <q-card-section class="q-gutter-sm">
          <q-input
            outlined
            label="Username"
            v-model="username"
          />
          <q-input
            outlined
            type="password"
            label="Password"
            v-model="password"
          />
        </q-card-section>
        <q-separator />
        <q-card-actions class="bg-grey-2">
          <q-btn
            flat
            type="submit"
            color="primary"
            label="login"
            :loading="isLoading"
          />
        </q-card-actions>
      </q-form>
    </q-card>
  </div>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      username: '',
      password: '',
      isLoading: false
    }
  },
  methods: {
    async handleSubmit () {
      this.isLoading = true
      try {
        const token = await this.$axios.post('http://localhost:8000/v1/auth/login', {
          username: this.username,
          password: this.password
        })
        this.$q.localStorage.set('token', token)
        this.$router.push({ name: 'home' })
      } catch (e) {
        console.error(e)
      } finally {
        this.isLoading = false
      }
    }
  }
}
</script>
