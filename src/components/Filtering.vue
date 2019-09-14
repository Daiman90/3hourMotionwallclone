<template>
  <div class="flex xs12 align-center md6">
    <v-select 
    v-model="value"
    :items="items"
    single-line
    hide-details>
    </v-select>
  </div>
</template>

<script>
export default {
  data: () => ({
    value: 'Recent',
    items: [
      'Recent',
      'Most downloaded',
      'Older'
    ]
  }),
  watch: {
    value: function() {
      this.$emit('value', this.value)
    }
  }
}
</script>

<style>

</style>