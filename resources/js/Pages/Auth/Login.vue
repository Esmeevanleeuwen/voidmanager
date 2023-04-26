<script setup>
import { ref } from 'vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

defineProps({
  canResetPassword: Boolean,
  status: String,
});

const form = useForm({
  email: '',
  password: '',
  remember: false,
});

const passwordFieldType = ref('password');

const togglePasswordVisibility = () => {
  passwordFieldType.value = passwordFieldType.value === 'password' ? 'text' : 'password';
};

const submit = () => {
  form
    .transform(data => ({
      ...data,
      remember: form.remember ? 'on' : '',
    }))
    .post(route('login'), {
      onFinish: () => form.reset('password'),
    });
};
</script>
<template>
  <div class="login-page">
    <Head title="Log in" />
    <div class="login-container">
      <!-- Login Form Column -->
      <div class="login-form">
        <div class="flex flex-col items-center">
          <img
          src="../../../images/logo.png"
          alt="Opening a door illustration"
          class="w-4/5"
        />
        </div>
        <form @submit.prevent="submit">
          <!-- Email Input Field -->
          <div class="input-field">
            <InputLabel for="email" value="Email" />
            <TextInput
              id="email"
              v-model="form.email"
              type="email"
              class="input"
              required
              autofocus
              autocomplete="username"
            />
            <InputError class="mt-2" :message="form.errors.email" />
          </div>
          <!-- Password Input Field -->
          <div class="input-field relative">
            <InputLabel for="password" value="Password" />
            <TextInput
              id="password"
              v-model="form.password"
              :type="passwordFieldType"
              class="input"
              required
              autocomplete="current-password"
            />
            <span class="password-eye" @click="togglePasswordVisibility">
              <!-- Eye icon, replace with your preferred icon library -->
              <i v-if="passwordFieldType === 'password'" class="far fa-eye"></i>
              <i v-else class="far fa-eye-slash"></i>
            </span>
            <InputError class="mt-2" :message="form.errors.password" />
          </div>
          <!-- Remember me Checkbox -->
          <div class="checkbox-label">
            <Checkbox
              v-model:checked="form.remember"
              name="remember"
              class="checkbox"
            />
            <span>Remember me</span>
          </div>
          <!-- Login Button and Forgot Password Link -->
          <div class="flex items-center justify-between">
            <Link
              v-if="canResetPassword"
              :href="route('password.request')"
              class="forgot-password"
            >
              Forgot your password?
            </Link>
            <PrimaryButton
              class="submit-btn"
              :class="{ 'opacity-25': form.processing }"
              :disabled="form.processing"
            >
              Log in
            </PrimaryButton>
          </div>
          <!-- Register Link -->
          <div class="flex  forgot-password mt-4">
            <Link :href="route('register')" class="underline">
              Don't have an account? Register now!
            </Link>
          </div>
        </form>
      </div>
      <!-- Image Column -->
      <div class="login-image px-8">
        <img
          src="../../../images/login.svg"
          alt="Opening a door illustration"
          class="w-4/5"
        />
      </div>
    </div>
  </div>
</template><style>
.login-page {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #ffffff;
}

.login-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-radius: 8px;
  padding: 32px;
  width: 100%;
  max-width: 900px;
}

.password-eye {
  position: absolute;
  right: 12px;
  top: 70%;
  transform: translateY(-50%);
  cursor: pointer;
}

@media (min-width: 768px) {
  .login-container {
    flex-direction: row;
  }
}

.login-form {
  width: 100%;
}

.login-form .input-field {
  margin-bottom: 16px;
}

.login-form .input {
  display: block;
  width: 100%;
  padding: 12px; 
  border-radius: 4px;
  background-color: #edf2f7 !important; /* Change the input background color */
  font-size: 14px;
  color: #333333;
  outline: none;
}

.login-form .input:focus {
  border-color: #38a169;
  box-shadow: 0 0 0 2px rgba(56, 161, 105, 0.3);
}
 

.login-image {
  display: none;
  justify-content: center;
  align-items: center;
  padding: 32px;
  width: 100%;
}

@media (min-width: 768px) {
  .login-image {
    display: flex;
  }
}

.login-image img {
  width: 130%;
  max-height: 500px; /* Set a max height for the image */
  margin-left: 200px;
}

img, video {
    max-width: 300%;
    height: auto;
}
</style>