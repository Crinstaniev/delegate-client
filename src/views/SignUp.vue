<template>
  <v-container class="pa-12" fluid>
    <v-row class="mb-4">
      <h3 class="title">Create a new account</h3>
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
            <v-text-field
              v-model="confirmPassword"
              :rules="confirmPasswordRules"
              label="Confirm Password"
              type="password"
              outlined
              required
            ></v-text-field>
            <div class="d-flex align-end checkbox-wrapper">
              <v-checkbox
                v-model="isAgreementChecked"
                :rules="agreeRules"
                required
              >
              </v-checkbox>
              <div>
                I agree to the
                <a href="#" @click.prevent="showConsentForm = true"
                  >experiment consent</a
                >
                by signing up for a new account.
              </div>
            </div>
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
          Already have an account? <router-link to="/login">Log in</router-link>
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
    <v-dialog v-model="showConsentForm" max-width="600px">
      <v-card>
        <v-card-title>
          Experiment Consent
        </v-card-title>
        <v-card-text> {{ lorem.generateParagraphs(8) }} </v-card-text>
        <v-btn color="#2D20F5" text @click="showConsentForm = false">OK</v-btn>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
import logo from '../assets/logo-light-mode.png';
import { LoremIpsum } from 'lorem-ipsum';

export default {
  data() {
    return {
      logo,
      valid: false,
      email: '',
      password: '',
      aggreementText: 'abaaba',
      confirmPassword: '',
      showConsentForm: true,
      isAgreementChecked: false,
      lorem: new LoremIpsum({
        sentencesPerParagraph: { max: 8, min: 4 },
        wordsPerSentence: { max: 16, min: 4 }
      }),
      passwordRules: [v => !!v || 'Password is required'],
      emailRules: [v => !!v || 'E-mail is required'],
      agreeRules: [v => !!v || ''],
      confirmPasswordRules: [
        v => !!(v === this.password) || 'Passwords are not consistent!'
      ]
    };
  },

  methods: {
    onSubmit() {
      let payload = {
        email: this.email,
        password: this.password
      };
      console.log(payload);
    },

    onConsentClicked() {
      console.log('abaaba');
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

.checkbox-wrapper {
  margin-top: -20px;
  margin-bottom: 20px;
}
</style>
