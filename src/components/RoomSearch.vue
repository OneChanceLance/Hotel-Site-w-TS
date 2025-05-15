<template>
  <div class="room-search">
    <div class="form-group">
      <label for="checkin">Check-in</label>
      <input type="date" id="checkin" v-model="checkIn" />
    </div>

    <div class="form-group">
      <label for="checkout">Check-out</label>
      <input type="date" id="checkout" v-model="checkOut" />
    </div>

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
  flex-direction:inherit;
  gap: 1.5rem;
  max-width: max-content;
  margin: 0 auto;
  padding: 2rem;
  border-radius: 12px;
  background-color: #ffffff;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.form-group {
  width: 200%;
  display: flex;
  flex-direction: row;

}

input,
select {
    width: 100%;
    padding: .55rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    color: #333;
    font-family: inherit;
}



/* Optional: highlight on hover (may not work in all browsers) */
select option:hover {
    background-color: #ffe5d0;
    color: #ff6600;
}


.search-button {
  width: 100%;
  background-color: #ff6600;
  color: #ffffff;
  padding: 0.85rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  font-size: 1rem;
  transition: background-color 0.25s ease;
}

.search-button:hover {
  background-color: #e75c00;
}
</style>