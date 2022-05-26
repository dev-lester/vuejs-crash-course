<template>
  <div class="p-grid">
    <div class="p-col-12 p-md-6 p-lg-3" v-for="pet in pets" :key="pet.id">
      <!-- <h3> {{ pet }} </h3> -->
      <Pet :pet="pet"/>
    </div>
  </div>
</template>

<script>
import Pet from "../components/Pet"

export default {
  props: {
    pets: Array
  },
  components: {
    Pet
  }
}
</script>

<style>

</style>