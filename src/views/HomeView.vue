<script setup>
import { ref } from "vue";

const requestData = ref();
const responseData = ref();

const fetchData = async () => {
  console.log("Fetching data for request count:", requestData.value);
  const response = await fetch(
    `http://localhost:1880/users?count=${requestData.value}`,
    {
      method: "GET",
    }
  );
  const data = await response.json();
  responseData.value = data;
};
</script>

<template>
  <div class="home">
    <div class="search-bar">
      <input type="text" placeholder="Search..." v-model="requestData" />
      <button @click="fetchData()">Search</button>
    </div>
    <div class="data-grid">
      {{ responseData }}
    </div>
  </div>
</template>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: calc(100vh - 32px);
  border: 1px solid gray;
  box-sizing: border-box;
}

.search-bar {
  width: 100%;
  height: 40px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  gap: 8px;
  padding: 0 8px;
  border: 1px solid red;
  box-sizing: border-box;
}

.search-bar input {
  width: 300px;
  height: 28px;
  padding: 0 8px;
}

.data-grid {
  flex: 1;
  width: 100%;
  border: 1px solid red;
  border-radius: 12px;
  box-sizing: border-box;
}
</style>