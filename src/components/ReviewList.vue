<template>
  <div class="review-container"></div>
</template>

<script>
export default {
  name: 'ReviewListComponent',
  props: {
    reviews: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style>

</style>