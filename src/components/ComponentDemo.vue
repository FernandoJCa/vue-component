<template>
  <Card class="w-[350px]">
    <CardHeader>
      <CardTitle>Interactive Component Demo</CardTitle>
      <CardDescription>Showcasing shadcn-vue components</CardDescription>
    </CardHeader>
    <CardContent>
      <div class="space-y-4">
        <div class="flex items-center justify-between">
          <Label for="count-input">Count</Label>
          <Input
              id="count-input"
              v-model.number="count"
              type="number"
              class="w-20 text-right"
          />
        </div>

        <div class="flex justify-between items-center">
          <Button @click="decrement" variant="outline" size="sm">-</Button>
          <span class="text-2xl font-bold" :class="{ 'text-green-500': isEvenHighlighted && isEven }">{{ count }}</span>
          <Button @click="increment" variant="outline" size="sm">+</Button>
        </div>

        <div class="flex items-center space-x-2">
          <Switch id="highlight-switch" v-model="isEvenHighlighted" />
          <Label for="highlight-switch">Highlight even numbers ({{ isEvenHighlighted ? 'On' : 'Off' }})</Label>
        </div>

        <Button @click="randomize" class="w-full" :variant="isEven ? 'default' : 'secondary'">
          Randomize
        </Button>

        <Alert v-if="showAlert" :variant="alertVariant">
          <AlertTitle>{{ alertTitle }}</AlertTitle>
          <AlertDescription>
            {{ alertDescription }}
          </AlertDescription>
        </Alert>
      </div>
    </CardContent>
    <CardFooter>
      <p class="text-sm text-muted-foreground" :class="{ 'text-green-500 font-bold': isEvenHighlighted && isEven }">
        {{ message }}
      </p>
    </CardFooter>
  </Card>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue'
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { Switch } from "@/components/ui/switch"
import { Alert, AlertTitle, AlertDescription } from "@/components/ui/alert"
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from "@/components/ui/card"
import { Label } from "@/components/ui/label"

const count = ref(0)
const isEvenHighlighted = ref(false)
const showAlert = ref(false)
const alertVariant = ref<'default' | 'destructive'>('default')
const alertTitle = ref('')
const alertDescription = ref('')

const increment = () => {
  count.value++
  console.log('Incremented. Count:', count.value, 'Is Even:', isEven.value, 'Highlighted:', isEvenHighlighted.value)
}
const decrement = () => {
  count.value--
  console.log('Decremented. Count:', count.value, 'Is Even:', isEven.value, 'Highlighted:', isEvenHighlighted.value)
}
const randomize = () => {
  count.value = Math.floor(Math.random() * 100)
  console.log('Randomized. Count:', count.value, 'Is Even:', isEven.value, 'Highlighted:', isEvenHighlighted.value)
}

const isEven = computed(() => count.value % 2 === 0)

const message = computed(() => {
  if (count.value === 0) return "Let's start counting!"
  if (count.value % 10 === 0) return "Wow! You hit a multiple of 10!"
  if (count.value < 0) return "Negative territory!"
  return isEven.value ? "That's an even number!" : "That's an odd number!"
})

watch(count, (newValue) => {
  console.log('Count changed to:', newValue, 'Is Even:', isEven.value, 'Highlighted:', isEvenHighlighted.value)
  if (newValue === 50) {
    showAlert.value = true
    alertVariant.value = 'default'
    alertTitle.value = 'Halfway there!'
    alertDescription.value = "You've reached 50. Keep it up!"
  } else if (newValue === 100) {
    showAlert.value = true
    alertVariant.value = 'destructive'
    alertTitle.value = 'Maximum reached!'
    alertDescription.value = "You've hit 100! Try going negative now."
  } else if (newValue === -10) {
    showAlert.value = true
    alertVariant.value = 'default'
    alertTitle.value = 'Negative milestone!'
    alertDescription.value = "You've reached -10. How low can you go?"
  } else {
    showAlert.value = false
  }
})

watch(isEvenHighlighted, (newValue) => {
  console.log('Highlight changed to:', newValue, 'Count:', count.value, 'Is Even:', isEven.value)
})
</script>