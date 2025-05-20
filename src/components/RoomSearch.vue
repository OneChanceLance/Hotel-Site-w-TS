<template>
  <div class="room-search">
    <div class="form-group">
      <label for="checkin">Check in</label>
      <input type="date" id="checkin" v-model="checkIn" />
    </div>
    <hr>
    <div class="form-group">
      <label for="checkout">Check-out</label>
      <input type="date" id="checkout" v-model="checkOut" />
    </div>
    <hr>
    <div class="form-group">
      <label for="guests">Guests</label>
      <select id="guests" v-model="guests">
        <option v-for="n in 10" :key="n" :value="n">{{ n }} Adult{{ n > 1 ? 's' : '' }}</option>
      </select>
    </div>

    <button class="search-button" @click="searchRooms">Search</button>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue';

  const checkIn = ref('');
  const checkOut = ref('');
  const guests = ref(2);

  function searchRooms() {
    console.log('Search Params:', {
      checkIn: checkIn.value,
      checkOut: checkOut.value,
      guests: guests.value
    });
  }
</script>

<style scoped>
  .room-search {
    display: flex;
    flex-direction: inherit;
    height: 3.25rem;
    max-height: max-content;
    gap: 1.5rem;
    max-width: max-content;
    margin: 0 auto;
    padding: 1rem;
    border-radius: 20px;
    background-color: #ffffff;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    width: 150%;
    align-items: flex-start;
    text-align: left;
  }

hr {
  width: 1px;
  height: 2.5rem; /* Adjust height as needed */
  border: none;
  border-left: 1px solid #c1c1c1;
  align-self: stretch;
}

  input {
    width: 90%;
    font-size: 1rem;
    font-weight: 600;
    border: 0px solid #ffffff;
    border-radius: 8px;
    background-color: #ffffff;
    color: #333;
    font-family: Arial;
  }

  label {
    color: #828282;
    font-weight: 100;
  }

  select {
    width: 100%;
    font-size: 1rem;
    font-weight: 600;
    border: 0px solid #ffffff;
    border-radius: 8px;
    background-color: #ffffff;
    color: #333;
    font-family: Arial, Helvetica, sans-serif;
  }



  /* Optional: highlight on hover (may not work in all browsers) */
  select option:hover {
    background-color: #ffe5d0;
    color: #ff6600;
  }


  .search-button {
    width: 100%;
    background-color: #e75c00;
    color: #ffffff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 500;
    
    font-size: 1.4rem;
    transition: background-color 0.25s ease;
  }

  .search-button:hover {
    background-color: #c34e00;
  }

  @media (max-width: 600px) {
    .room-search {
      flex-direction: column;
      height: auto;
      max-width: 70vw;      /* Make it wider on mobile */
      width: 95vw;          /* Ensure width is set */
      gap: 0.75rem;
      padding: 0.5rem;
    }
    .form-group {
      width: 100%;
    }
    .search-button {
      width: 100%;
    }
    hr {
      width: 100%;
      border: none;
      border-top: 1.5px solid #e0e0e0; /* More visible horizontal line */
      margin: 0.5rem 0;
    }
  }
</style>