<template>
      <h1 id='login'>Welcome to the Hardware Security Key Testing Website!</h1>
  <div class="form-container" id='login'>
    <h2>Log In / Register</h2>

    <form @submit.prevent="loginUser" class="form" id='login'>
      <div id='login'>
        <label for="username">Username:</label>
        <input type="username" id="username" v-model="username" required />
      </div>
      <div id='login'>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />
      </div id='login'>
      <button type="submit" class="form-btn" :disabled="isLoading">
        {{ isLoading ? "Logging in..." : "Log In" }}
      </button>
      <button type="submit" class="form-btn" :disabled="isLoading">
        {{ isLoading ? "Registering..." : "Register" }}
      </button>
    </form>

    <p class="success-message" v-if="successMessage">{{ successMessage }}</p>
    <p class="error-message" v-if="errorMessage">{{ errorMessage }}</p>
  </div>

    <div id='login'>
      <v-btn :href="`${apiOrigin}/api/v1/auth/google`" color="primary">
        <v-icon left>mdi-google</v-icon>
         Log In with Google
      </v-btn>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Login',
    data: () => ({
      apiOrigin: process.env.VUE_APP_API_ORIGIN
    })
  }
  </script>
  
  <style scoped>
  #login {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 50%;
    justify-content: space-evenly;
    }

  .form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
  padding: 5px;
  background-color: #1967C0; /* Bue background */
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.19), 0px 6px 6px rgba(0, 0, 0, 0.23);
  box-sizing: border-box; 
}

h2 {
  text-align: center;
  color: #ddd; /* Lighter text */
}

.form {
  display: flex;
  flex-direction: column;
  width: 100%;
}

label {
  font-size: 1.1em;
  margin-bottom: 5px;
  color: #ddd; /* Lighter text */
}

input {
  padding: 10px;
  font-size: 1em;
  border: 1px solid #aaa; /* Lighter border */
  border-radius: 5px;
  outline: none;
  width: 100%;
  box-sizing: border-box; 
  background-color: #E8E9EB; /* Light input background */
  color: #000000; /* Black input text */
}

input:focus {
  border-color: #42b983;
}

.form-btn {
  display: flex;
  flex-direction: row;
  padding: 5px 10px 5px 10px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid #E8E9EB;
  border-radius: 32px;
  color: #E8E9EB;
  transition: 0.2s ease-in-out;
}

.form-btn:hover {
  border: 2px solid #CBCBCB;
  color: #CBCBCB;
}

.error-message {
  color: #a94442;
  background-color: #4a4a4a; /* Darker background */
  border-color: #ebccd1;
}
  </style>