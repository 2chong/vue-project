<script setup>
 fetch('http://127.0.0.1:1880/users')
  .then(response => response.json())
  .then(data => {
    data.forEach(row => {
      if (row.value > 20) {
        console.log(row.value)
      }
    })
  });

</script>

<template>
  <div class="about">
    <h1>Test Page</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
