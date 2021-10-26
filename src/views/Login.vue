<template>
  <v-container class="pa-12" fluid>
    <v-row class="mb-4">
      <h3 class="title">Welcome to our test! Please log in to your account</h3>
    </v-row>
    <v-row justify="center">
      <v-col cols="auto" class="mt-6">
        <v-img :src="logo" width="150px"> </v-img>
      </v-col>
    </v-row>
    <v-row justify="center">
      <div class="input-wrapper">
        <v-col cols="12">
          <v-form v-model="valid" @submit.prevent="onSubmit">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              outlined
              required
            ></v-text-field>
            <v-text-field
              v-model="password"
              :rules="passwordRules"
              label="Password"
              type="password"
              outlined
              required
            ></v-text-field>
            <v-btn block :disabled="!valid" type="submit" color="#2D20F5">
              <div style="color: white">Login</div>
            </v-btn>
          </v-form>
        </v-col>
      </div>
    </v-row>
    <v-row justify="center">
      <v-col cols="auto">
        <p>
          Don't have an account? <router-link to="/signup">Sign up</router-link>
        </p>
      </v-col>
    </v-row>
    <v-row justify="center">
      <div class="mb-3 mt-5 description">
        If you have any question, concern, or suggestion, please contact
        jz294@duke.edu
      </div>
    </v-row>
    <v-row justify="center">
      <div class="description">
        © Copyright SciEcon TEA Taskforce, All Rights Reserved.
      </div>
    </v-row>
  </v-container>
</template>

<script>
import logo from '../assets/logo-light-mode.png';

export default {
  data() {
    return {
      logo,
      valid: false,
      email: '',
      password: '',
      passwordRules: [v => !!v || 'Password is required'],
      emailRules: [v => !!v || 'E-mail is required']
    };
  },

  methods: {
    onSubmit() {
      let payload = {
        email: this.email,
        password: this.password
      };
      console.log(payload);
    }
  }
};
</script>

<style>
.input-wrapper {
  width: 450px;
}

.description {
  opacity: 0.6;
  font-size: 14px;
}
</style>
