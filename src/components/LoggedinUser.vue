<template lang="html">
  <q-list>
    <q-item class="q-px-none">
      <q-item-section side>
        <q-avatar
          size="32px"
          color="secondary"
          text-color="white"
          class="text-uppercase"
          v-if="!isLoading"
        >
          {{ user.email.charAt(0) }}
        </q-avatar>
        <q-skeleton
          size="32px"
          type="QAvatar"
          v-else
        />
      </q-item-section>
      <q-item-section>
        <div v-if="!isLoading">
          <q-item-label class="text-grey-8">Comment as</q-item-label>
          <q-item-label class="text-weight-bold text-subtitle1">
            {{ user.email }}
          </q-item-label>
        </div>
        <div v-else>
          <q-skeleton type="text"/>
          <q-skeleton type="text"/>
        </div>
      </q-item-section>
      <q-item-section side>
        <q-btn
          flat
          dense
          color="primary"
          label="Logout"
          @click="handleLogout"
        />
      </q-item-section>
    </q-item>
  </q-list>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      user: {},
      isLoading: false
    }
  },
  methods: {
    handleLogout () {
      this.$q.localStorage.remove('token')
      this.$router.push({ name: 'login' })
    },
    async handleFetchUser () {
      this.isLoading = true
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
        this.isLoading = false
      }
    }
  },
  created () {
    this.handleFetchUser()
  }
}
</script>
