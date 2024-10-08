<template>
  <div>
    <h1>Current Autobot Count: {{ autobotCount }}</h1>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { io, Socket } from 'socket.io-client';

// Reactive reference to store the count of Autobots
const autobotCount = ref(0);
let socket:Socket;

// Function to fetch the initial count from the server
const fetchInitialCount = async () => {
  try {
    const response = await fetch('http://localhost:3500/api/v1/autobot/generateAutobots'); // Replace with your actual API endpoint
    const data = await response.json();
    autobotCount.value = data.count || 0;
  } catch (error) {
    console.error('Failed to fetch initial count:', error);
  }
};

onMounted(() => {
  socket = io('http://localhost:3500'); 

  // Listen for updates from the server
  socket.on('autobotCountUpdated', (count) => {
    autobotCount.value = count;
  });

  // Fetch the initial count of Autobots
  fetchInitialCount();
});

onUnmounted(() => {
  if (socket) {
    socket.disconnect();
  }
});
</script>

<style scoped>
.item {
  margin-top: 2rem;
  display: flex;
  position: relative;
}

.details {
  flex: 1;
  margin-left: 1rem;
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  color: var(--color-text);
}

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

@media (min-width: 1024px) {
  .item {
    margin-top: 0;
    padding: 0.4rem 0 1rem calc(var(--section-gap) / 2);
  }

  i {
    top: calc(50% - 25px);
    left: -26px;
    position: absolute;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 50px;
    height: 50px;
  }

  .item:before {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:after {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:first-of-type:before {
    display: none;
  }

  .item:last-of-type:after {
    display: none;
  }
}
</style>
