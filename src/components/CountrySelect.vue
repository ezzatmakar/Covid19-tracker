<template>
  <select v-model="selected" class="text-center rounded w-full p-2">
    <option value="0" class="form-select mt-10 block w-full border p-3 rounded">
      Select Country
    </option>
    <option v-for="country in countries" :value="country.ID">
      {{country.Country}}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ['countries'],
  data() {
    return {
      selected: 0
    }
  }
}
</script>

<style scoped>

</style>