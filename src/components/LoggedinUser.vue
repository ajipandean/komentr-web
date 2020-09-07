<template lang="html">
  <q-list>
    <q-item class="q-px-none">
      <q-item-section avatar>
        <q-avatar
          color="accent"
          text-color="white"
        >M</q-avatar>
      </q-item-section>
      <q-item-section>
        <q-item-label class="text-weight-medium text-subtitle1">
          ajikun
        </q-item-label>
        <q-item-label class="text-grey-8">ajikun@gmail.com</q-item-label>
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
  </q-list>
</template>

<script type="text/javascript">
export default {
  methods: {
    handleLogout () {
      this.$q.localStorage.remove('token')
      this.$router.push({ name: 'login' })
    }
  }
}
</script>
