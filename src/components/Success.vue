<script setup>
  defineProps({
    email: {
      type: String,
      required: true
    }
  })

  defineEmits(['dismiss-message'])
</script>

<template>
  <div class="h-[100dvh] sm:h-[32.5rem] w-full sm:max-w-[31.25rem] bg-custom-white text-custom-blue-800 flex flex-col justify-between px-[1rem] py-[2rem] sm:p-[4rem] sm:rounded-4xl shadow-2xl">
    <div class="mt-[10rem] sm:mt-0 space-y-8">
      <img src="/assets/images/icon-success.svg" alt="" class="w-[4rem]">
      
      <h2 class="font-bold text-4xl sm:text-5xl">Thanks for subscribing!</h2>
    
      <p>A confirmation email has been sent to <a href="https://mail.google.com" target="_blank" class="font-bold hover:opacity-75 duration-250">{{ email }}</a>. 
      Please open it and click the button inside to confirm your subscription.</p>
    </div>
  
    <button 
      aria-label="Dismiss message button"
      class="bg-custom-blue-800 text-custom-white font-bold py-4 rounded-md hover:bg-custom-red hover:shadow-2xl hover:shadow-custom-red cursor-pointer duration-250"
      @click="$emit('dismiss-message')"
    >
      Dismiss message
    </button>
  </div>
</template>