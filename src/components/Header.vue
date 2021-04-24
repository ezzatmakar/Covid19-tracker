<template>
  <header class="text-center bg-indigo-900 text-white p-4 mb-10">
    <div class="text-3xl md:text-5xl font-bld mb-3"><i class="fas fa-viruses"></i> Covid-19 Tracker</div>
    <p>
      API by 
      <a class="text-red-400 hover:text-green-500" href="https://covid19api.com" target="_blank" rel="noopener noreferrer">covid19api.com</a>
    </p>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
.fa-viruses:before{
  color: #b91c1c;
}
p{
  display:inline;
  word-wrap: break-word;  
}
p:first-of-type{
  margin-right: 15px;
}
</style>