<script setup>
  defineProps({
    email: {
      type: String,
      required: true
    },
    error: {
      type: Boolean,
      required: true
    },
  })

  defineEmits(['update:email', 'validate-form'])
</script>

<template>
  <main
    class="w-full max-sm:min-h-[53.125rem] max-sm:h-[100dvh] sm:h-[40rem] max-w-[58.125rem] bg-custom-white sm:flex flex-row-reverse sm:py-[1.5rem] sm:pr-[1.5rem] sm:rounded-4xl shadow-2xl"
  >
    <div class="sm:w-[40%] sm:bg-[url(/assets/images/illustration-sign-up-desktop.svg)] bg-cover bg-center bg-no-repeat sm:rounded-2xl">
      <img
        src="/assets/images/illustration-sign-up-mobile.svg"
        alt=""
        class="w-full sm:hidden"
      >
    </div>

    <div class="sm:w-[60%] text-custom-blue-800 px-[2rem] py-[2rem] sm:p-0 space-y-6 sm:flex sm:flex-col justify-center sm:px-[4rem]">
      <h1 class="font-bold text-4xl lg:text-[3.5rem]">Stay updated!</h1>
      <p class="text-base">Join 60,000+ product managers receiving monthly updates on:</p>

      <ul class="space-y-4">
        <li class="flex items-start gap-4">
          <img src="/assets/images/icon-list.svg" alt="">
          <p>Product discovery and building what matters</p>
        </li>
        <li class="flex items-start gap-4">
          <img src="/assets/images/icon-list.svg" alt="">
          <p>Measuring to ensure updates are a success</p>
        </li>
        <li class="flex items-start gap-4">
          <img src="/assets/images/icon-list.svg" alt="">
          <p>And much more!</p>
        </li>
      </ul>

      <form
        class="grid"
        @submit.prevent="$emit('validate-form')"
        novalidate
      >
        <div class="mb-2 text-sm font-bold flex justify-between">
          <label
            for="email"
          >
            Email address
          </label>

          <p 
            v-if="error"
            class="text-custom-red"
          >
            Valid email required
          </p>
        </div>
        <input
          type="email"
          id="email"
          autocomplete="on"
          placeholder="email@company.com"
          class="border-1 border-custom-grey rounded-md px-[1.25rem] py-[.75rem] mb-8 focus:outline-1 focus:outline-custom-blue-700 cursor-pointer"
          :class="[error ? 'border-custom-red bg-red-100 text-custom-red' : '']"
          :value="email"
          @input="$emit('update:email', $event.target.value)"
        >
        <button
          aria-label="Subscribe button"
          class="bg-custom-blue-800 text-custom-white font-bold px-[1rem] py-4 rounded-md hover:bg-custom-red hover:shadow-2xl hover:shadow-custom-red cursor-pointer duration-250"
        >Subscribe to monthly newsletter</button>
      </form>
    </div>
  </main>
</template>