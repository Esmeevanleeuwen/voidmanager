<script setup>
import { ref } from 'vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    account_type: 'basic',
});

const passwordFieldType = ref('password');
const passwordConfirmationFieldType = ref('password');

const togglePasswordVisibility = () => {
    passwordFieldType.value = passwordFieldType.value === 'password' ? 'text' : 'password';
};

const togglePasswordConfirmationVisibility = () => {
    passwordConfirmationFieldType.value = passwordConfirmationFieldType.value === 'password' ? 'text' : 'password';
};

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script><template>
    <div class="register-page">
      <Head title="Register" />
      <div class="register-container">
        <!-- Register Form Column -->
        <div class="register-form">
          <div class="flex flex-col items-center">
            <AuthenticationCardLogo />
          </div>
          <form @submit.prevent="submit">
            <!-- Name Input Field -->
            <div class="input-field">
              <InputLabel for="name" value="Name" />
              <TextInput
                id="name"
                v-model="form.name"
                type="text"
                class="input"
                required
                autofocus
                autocomplete="name"
              />
              <InputError class="mt-2" :message="form.errors.name" />
            </div>
            <!-- Email Input Field -->
            <div class="input-field">
              <InputLabel for="email" value="Email" />
              <TextInput
                id="email"
                v-model="form.email"
                type="email"
                class="input"
                required
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
                autocomplete="new-password"
              />
              <span class="password-eye" @click="togglePasswordVisibility">
                <!-- Eye icon, replace with your preferred icon library -->
                <i v-if="passwordFieldType === 'password'" class="far fa-eye"></i>
                <i v-else class="far fa-eye-slash"></i>
              </span>
              <InputError class="mt-2" :message="form.errors.password" />
            </div>
            <!-- Confirm Password Input Field -->
            <div class="input-field relative">
              <InputLabel for="password_confirmation" value="Confirm Password" />
              <TextInput
                id="password_confirmation"
                v-model="form.password_confirmation"
                :type="passwordConfirmationFieldType"
                class="input"
                required
                autocomplete="new-password"
              />
              <span class="password-eye" @click="togglePasswordConfirmationVisibility">
                <!-- Eye icon, replace with your preferred icon library -->
                <i v-if="passwordConfirmationFieldType === 'password'" class="far fa-eye"></i>
                <i v-else class="far fa-eye-slash"></i>
              </span>
              <InputError class="mt-2" :message="form.errors.password_confirmation" />
            </div>
            <!-- Account Type Dropdown -->
            <div class="input-field">
              <InputLabel for="account_type" value="Account Type" />
              <select id="account_type" v-model="form.account_type" class="input">
                <option value="basic">Basic</option>
                <option value="pro">Pro</option>
              </select>
              <InputError class="mt-2" :message="form.errors.account_type" />
            </div>
            <!-- Submit Button -->
            <div class="flex items-center justify-end mt-4">
              <Link :href="route('login')" class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                Already registered?
              </Link>
   
              <PrimaryButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
              Register
            </PrimaryButton>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
  

<style scoped>
.register-page {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f3f4f6;
}

.register-container {
  width: 100%;
  max-width: 480px;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 2rem;
}

.input-field {
  margin-bottom: 1.5rem;
}

.input {
  width: 100%;
  border: 1px solid #e2e8f0;
  border-radius: 4px;
  padding: 0.5rem 0.75rem;
  background-color: #f5f5f5;
  color: #1a202c;
}

.input:focus {
  outline: none;
  border-color: #a0aec0;
  box-shadow: 0 0 0 3px rgba(168, 175, 192, 0.4);
}

.password-eye {
  position: absolute;
  top: 50%;
  right: 0.75rem;
  transform: translateY(-50%);
  cursor: pointer;
}

.primary-button {
  background-color: #667eea;
  color: #ffffff;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.primary-button:hover {
  background-color: #5a67d8;
}

.primary-button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.4);
}

.primary-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
