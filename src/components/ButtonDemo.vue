<template>
  <div class="p-8 max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden">
    <h1 class="text-3xl font-bold mb-6 text-center text-gray-800">Interactive Button Demo</h1>

    <div class="mb-6 text-center">
      <p class="text-4xl font-bold mb-2">{{ count }}</p>
      <p class="text-gray-600">Current Count</p>
    </div>

    <div class="space-y-4">
      <Button @click="increment" class="w-full">Increment</Button>
      <Button @click="decrement" variant="destructive" class="w-full">Decrement</Button>
      <Button @click="reset" variant="outline" class="w-full">Reset</Button>
    </div>

    <div class="mt-6 space-x-2 flex justify-center">
      <Button @click="toggleColor" :variant="colorVariant" size="sm">
        Toggle Color
      </Button>
      <Button @click="randomize" variant="secondary" size="sm">Randomize</Button>
    </div>

    <div class="mt-6">
      <p class="text-sm text-gray-600 text-center" :class="{ 'animate-bounce': count % 10 === 0 }">
        {{ message }}
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import { Button } from "@/components/ui/button"

const count = ref(0)
const colorVariant = ref<'default' | 'destructive'>('default')

const increment = () => count.value++
const decrement = () => count.value--
const reset = () => count.value = 0
const toggleColor = () => colorVariant.value = colorVariant.value === 'default' ? 'destructive' : 'default'
const randomize = () => count.value = Math.floor(Math.random() * 100)

const message = computed(() => {
  if (count.value === 0) return "Let's start counting!"
  if (count.value % 10 === 0) return "Wow! You hit a multiple of 10!"
  if (count.value < 0) return "Negative territory!"
  return "Keep going!"
})
</script>