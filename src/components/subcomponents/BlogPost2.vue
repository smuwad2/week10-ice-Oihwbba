<template>
  <div class="card mb-3" style="max-width: 20rem;">
    <!-- Image -->
    <img
      :src="imgLoc"
      class="card-img-top"
      :alt="`Mood image: ${mood}`"
    />

    <div class="card-body">
      <!-- Title -->
      <h5 class="card-title">{{ subject }}</h5>

      <!-- Entry text -->
      <p class="card-text">{{ entry }}</p>
    </div>

     <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    subject: String,
    entry: String,
    mood: String,
  },
  computed: {
    imgLoc() {
      // Use plain template literal for image path
      return `/assets/${this.mood.toLowerCase()}.png`
    },
  },
}
</script>
 