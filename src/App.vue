<template>
  <div class="p-5">
    <div class="row q-col-gutter-md">
      <div class="col-12">
        <q-btn 
          label="Open User Form" 
          color="primary" 
          icon="person_add"
          @click="modalRef?.show()" 
        />
      </div>
    </div>
    
    <AnqModalForm
      ref="modalRef"
      title="User Registration"
      :persistent="true"
      @submit="onSubmit"
      @hide="onModalHide"
    >
      <template #content>
        <div class="q-pa-md">
          <q-form @submit="onSubmit" class="q-gutter-md">
            <div class="row q-col-gutter-md">
              <div class="col-12 col-md-6">
                <q-input
                  v-model="formData.firstName"
                  label="First Name"
                  :rules="[val => !!val || 'First name is required']"
                  outlined
                />
              </div>
              <div class="col-12 col-md-6">
                <q-input
                  v-model="formData.lastName"
                  label="Last Name"
                  :rules="[val => !!val || 'Last name is required']"
                  outlined
                />
              </div>
            </div>

            <q-input
              v-model="formData.email"
              label="Email"
              type="email"
              :rules="[
                val => !!val || 'Email is required',
                val => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(val) || 'Invalid email format'
              ]"
              outlined
            />

            <q-select
              v-model="formData.role"
              :options="roleOptions"
              label="Role"
              :rules="[val => !!val || 'Role is required']"
              outlined
            />

            <q-input
              v-model="formData.password"
              label="Password"
              type="password"
              :rules="[
                val => !!val || 'Password is required',
                val => val.length >= 8 || 'Password must be at least 8 characters'
              ]"
              outlined
            />

            <q-toggle
              v-model="formData.terms"
              label="I agree to the terms and conditions"
              :rules="[val => val || 'You must accept the terms']"
            />
          </q-form>
        </div>
      </template>
    </AnqModalForm>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
import { AnqModalForm } from './index';

const modalRef = ref<InstanceType<typeof AnqModalForm> | null>(null);

const formData = reactive({
  firstName: 'John',
  lastName: 'Doe',
  email: 'john.doe@example.com',
  role: 'user',
  password: 'SecurePass123!',
  terms: true
});

const roleOptions = [
  { label: 'Admin', value: 'admin' },
  { label: 'User', value: 'user' },
  { label: 'Guest', value: 'guest' }
];

const onSubmit = () => {
  console.log('Form submitted:', formData);
  alert('Form submitted');
  modalRef.value?.hide();
};

const onModalHide = () => {
  // Reset form data when modal is closed
  Object.keys(formData).forEach(key => {
    if (key === 'terms') {
      formData[key] = false;
    } else {
      formData[key] = '';
    }
  });
  console.log('Modal hidden');
};
</script>

<style scoped>
.q-form {
  max-width: 800px;
  margin: 0 auto;
}
</style>