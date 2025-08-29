<script setup lang="ts">
import Navbar from '@/components/Navbar.vue'
import { Button } from '@/components/ui/button'
</script>

<template>
  <Navbar />
  <div id="inicio" class="w-full bg-background py-12 min-h-screen flex items-center justify-center">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 container mx-auto px-4">
      <div class="flex flex-col gap-4 justify-center">
        <h1 class="text-5xl text-foreground font-bold">
          Título Focado no Problema que você Resolve
        </h1>
        <p class="text-foreground text-lg mt-4">
          Descreva de forma breve e direta o que é o seu produto, pra quem ele é e o que torna ele
          tão especial.
        </p>
        <a href="/" class="w-fit">
          <Button variant="default" class="p-6 text-lg font-bold"> CTA Principal </Button>
        </a>
        <p class="text-foreground text-sm mt-4">SOCIAL PROOF (QUEM USA O SEU PRODUTO)</p>
        <div class="overflow-hidden w-full">
          <div class="flex gap-6 items-center animate-logo-slide" style="width: max-content">
            <!-- Repeat for seamless loop -->
            <template v-for="i in [1, 2]" :key="i">
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user1" />
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user2" />
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user3" />
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user4" />
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user5" />
              <img class="rounded-lg" src="https://placehold.co/150x75" alt="user6" />
            </template>
          </div>
        </div>
      </div>
      <div class="flex items-center justify-center">
        <img class="object-cover rounded-lg" src="https://placehold.co/576" alt="logo" />
      </div>
    </div>
  </div>
  <div id="sobre" class="w-full bg-primary py-12 min-h-screen flex items-center justify-center">
    <div class="flex items-center justify-center h-full">
      <h1 class="text-4xl text-secondary font-bold">Sobre</h1>
    </div>
  </div>
  <div id="precos" class="w-full bg-background py-12 min-h-screen flex items-center justify-center">
    <div class="flex items-center justify-center h-full">
      <h1 class="text-4xl text-primary font-bold">Preços</h1>
    </div>
  </div>
  <div id="contato" class="w-full bg-primary py-12 min-h-screen flex items-center justify-center">
    <div class="flex items-center justify-center h-full">
      <h1 class="text-4xl text-secondary font-bold">Contato</h1>
    </div>
  </div>
  <div id="ajuda" class="w-full bg-background py-12 min-h-screen flex items-center justify-center">
    <div class="flex items-center justify-center h-full">
      <h1 class="text-4xl text-primary font-bold">Ajuda</h1>
    </div>
  </div>
</template>

<style scoped>
@keyframes logo-slide {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
.animate-logo-slide {
  animation: logo-slide 20s linear infinite;
}
</style>
