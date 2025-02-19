<template>
    <div>
      <h1>Background Checkings</h1>
      <ul>
        <li v-for="checking in backgroundCheckings" :key="checking.id">
          <h3>{{ checking.candidate.name }}</h3>
          <p>Email: {{ checking.candidate.email }}</p>
          <p>Phone: {{ checking.candidate.phone }}</p>
          <p>Status: {{ checking.checking_status }}</p>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        backgroundCheckings: []
      };
    },
    async created() {
      try {
        const response = await axios.get(
          'https://9093-103-19-78-162.ngrok-free.app/api/v1/background-checkings?page=1&perPage=10',
          {
            headers: {
              Authorization: 'Bearer 37|eVBo4DanJRcOC7gbt7EqU1CBUgnWhe8HVW4wuaaNb853429c'
            }
          }
        );
        this.backgroundCheckings = response.data.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
  };
  </script>
  
  <style scoped>
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
  }
  h3 {
    margin: 0;
  }
  p {
    margin: 5px 0;
  }
  </style>
  