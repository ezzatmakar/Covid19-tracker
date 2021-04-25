<template>
  <div class="text-center">
    <select
      v-model="selected"
      class="shadow-md bg-blue-100 text-gray-700 border-none inline-block py-3 pl-3 pr-8 rounded leading-tight"
    >
      <option
        value="0"
        class="form-select mt-10 block w-full border p-3 rounded"
      >
        Select Country
      </option>
      <option v-for="country in countries" :key="country.ID">
        {{ country.Country }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
};
</script>

<style scoped>
</style>