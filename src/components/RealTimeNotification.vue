<template>
    <div>
      <h1>Real-Time Notifications</h1>
      <p v-if="notification">New Notification: {{ notification }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        notification: null,
      };
    },
    mounted() {
      // Listening for Pusher events on the Broadcast channel
      window.Echo.channel('brt_creation')
        .listen('BRTCreated', (event) => {
            console.log("EVENT:",  event);
          this.notification = event.message;  
        });
    }
  };
  </script>
  