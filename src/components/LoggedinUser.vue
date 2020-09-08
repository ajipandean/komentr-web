<template lang="html">
  <q-list
    class="relative-position"
    v-if="!visible"
  >
    <q-item class="q-px-none">
      <q-item-section avatar>
        <q-avatar
          color="accent"
          text-color="white"
          class="text-uppercase"
        >
          {{ user.username.charAt(0) }}
        </q-avatar>
      </q-item-section>
      <q-item-section>
        <q-item-label class="text-weight-medium text-subtitle1">
          {{ user.username }}
        </q-item-label>
        <q-item-label class="text-grey-8">{{ user.email }}</q-item-label>
      </q-item-section>
      <q-item-section side>
        <q-btn
          flat
          color="primary"
          label="logout"
          @click="handleLogout"
        />
      </q-item-section>
    </q-item>
    <q-inner-loading :showing="visible">
      <q-spinner
        size="2em"
        color="primary"
      />
    </q-inner-loading>
  </q-list>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      user: {},
      visible: false,
      pageLoading: false
    }
  },
  methods: {
    handleLogout () {
      this.$q.localStorage.remove('token')
      this.$router.push({ name: 'login' })
    },
    async fetchLoggedInUser () {
      this.visible = true
      try {
        const token = this.$q.localStorage.getItem('token')
        const { data } = await this.$axios.get('http://localhost:8000/v1/secure/user', {
          headers: {
            Authorization: `Bearer ${token}`
          }
        })
        this.user = data
      } catch (e) {
        console.error(e)
      } finally {
        this.visible = false
      }
    }
  },
  created () {
    this.fetchLoggedInUser()
  }
}
</script>
