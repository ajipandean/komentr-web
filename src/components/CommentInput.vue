<template lang="html">
  <div class="q-my-sm">
    <q-input
      rounded
      outlined
      autogrow
      placeholder="Write your comment..."
    >
      <template v-slot:prepend>
        <q-btn
          flat
          round
          icon="emoji_emotions"
        />
      </template>
      <template v-slot:append>
        <q-btn
          flat
          round
          icon="photo"
        />
        <q-btn
          flat
          round
          color="primary"
          icon="send"
        />
      </template>
    </q-input>
  </div>
</template>
