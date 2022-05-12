<template>
  <div class="message-box">
    <p class="message">{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    message: String,
  },
};
</script>

<style scoped>
.message-box {
  background-color: #cce5ff;
  border: 2px solid #b8daff;
  border-radius: 5px;
  padding: 1rem;
  max-width: 40rem;
  margin: 1.8rem auto;
}

.message {
  font-size: 1.8rem;
  color: #004085;
}
</style>
