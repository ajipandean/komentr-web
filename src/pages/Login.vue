<template lang="html">
  <div class="flex flex-center fullscreen">
    <q-card style="width:400px;max-width: 500px;">
      <q-card-section class="q-pb-none">
        <div class="text-h6">Welcome</div>
      </q-card-section>
      <q-form>
        <q-card-section class="q-gutter-sm">
          <q-input
            outlined
            label="Username"
          />
          <q-input
            outlined
            label="Password"
          />
        </q-card-section>
        <q-separator />
        <q-card-actions class="bg-grey-2">
          <q-btn
            flat
            color="primary"
            label="login"
          />
        </q-card-actions>
      </q-form>
    </q-card>
  </div>
</template>
