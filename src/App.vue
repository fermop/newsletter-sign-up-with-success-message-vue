<script setup>
  import { ref } from 'vue';
  import Form from './components/Form.vue';
  import Spinner from './components/Spinner.vue';
  import Success from './components/Success.vue';
  import Footer from './components/Footer.vue';

  const email = ref('')
  const error = ref(false)
  const success = ref(false)
  const loading = ref(false)

  const validateForm = () => {
    // Validate email
    const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
    if (!regex.test(email.value)) {
      error.value = true
      return
    }

    success.value = true
    loading.value = true
    error.value = false

    setTimeout(() => {
      loading.value = false
    }, 1500)
  }

  const dismissMessage = () => {
    loading.value = true
    
    setTimeout(() => {
      email.value = ''
      loading.value = false
      success.value = false
    }, 1500)
  }
</script>

<template>
  <div class="min-h-[100dvh] flex flex-col items-center justify-center  sm:p-4 lg:p-0">
    <Form
      v-if="!success"
      v-model:email="email"
      :error="error"
      @validate-form="validateForm"
    />

    <Spinner v-if="loading"/>

    <Success 
      v-if="success && !loading"
      :email="email"
      @dismiss-message="dismissMessage"
    />
  </div>
  
  <Footer class=""/>
</template>