<script setup lang="ts">
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import logo from '@/assets/logo.svg'
import { RouterLink, useRouter } from 'vue-router'
import { LucideAtSign, LucideWind, LucideZap } from 'lucide-vue-next'

const router = useRouter()

const isMobileMenuOpen = ref(false)

const links = [
  {
    label: 'Início',
    href: '#inicio',
  },
  {
    label: 'Sobre',
    href: '#sobre',
  },
  {
    label: 'Preços',
    href: '#precos',
  },
  {
    label: 'Contato',
    href: '#contato',
  },
  {
    label: 'Ajuda',
    href: '#ajuda',
  },
]

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

// Função para scroll suave animado
const smoothScrollTo = (href: string) => {
  const targetId = href.replace('#', '')
  const targetElement = document.getElementById(targetId)

  if (targetElement) {
    // Fecha o menu mobile se estiver aberto
    closeMobileMenu()

    const targetPosition = targetElement.offsetTop

    // Scroll suave com easing
    window.scrollTo({
      top: targetPosition,
      behavior: 'smooth',
    })
  }
}
</script>

<template>
  <nav class="w-full p-2 border-b shadow-sm border-gray-100 bg-background">
    <div class="flex items-center justify-between container mx-auto px-4">
      <!-- Logo -->
      <div class="flex items-center gap-2">
        <a href="/" @click="closeMobileMenu">
          <LucideAtSign class="w-16 h-16 text-primary" />
        </a>
      </div>

      <!-- Desktop Navigation -->
      <div class="hidden md:flex items-center gap-2">
        <template v-for="link in links" :key="link.href">
          <Button
            as-child
            variant="link"
            class="text-foreground hover:text-primary transition-colors duration-200"
            @click="smoothScrollTo(link.href)"
          >
            <a :href="link.href" @click.prevent="smoothScrollTo(link.href)">
              {{ link.label }}
            </a>
          </Button>
        </template>
      </div>

      <!-- Mobile Menu Button -->
      <div class="md:hidden">
        <Button
          variant="ghost"
          size="sm"
          @click="toggleMobileMenu"
          class="p-2"
          :aria-expanded="isMobileMenuOpen"
          aria-label="Toggle mobile menu"
        >
          <svg
            class="w-6 h-6 transition-transform duration-200"
            :class="{ 'rotate-90': isMobileMenuOpen }"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              v-if="!isMobileMenuOpen"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </Button>
      </div>
    </div>

    <!-- Mobile Navigation Menu -->
    <div
      v-if="isMobileMenuOpen"
      class="md:hidden absolute top-16 left-0 right-0 bg-background border-b border-gray-100 shadow-lg"
    >
      <div class="container mx-auto px-4 py-4">
        <div class="flex flex-col space-y-2">
          <template v-for="link in links" :key="link.href">
            <Button
              as-child
              variant="ghost"
              class="w-full justify-start text-foreground hover:text-primary hover:bg-accent transition-colors duration-200"
              @click="smoothScrollTo(link.href)"
            >
              <a :href="link.href" @click.prevent="smoothScrollTo(link.href)">
                {{ link.label }}
              </a>
            </Button>
          </template>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Smooth transitions for mobile menu */
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* Smooth scroll behavior global */
html {
  scroll-behavior: smooth;
}

/* Custom scroll animation with easing */
@keyframes smoothScroll {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-100px);
  }
}

/* Hover effects for navigation links */
.nav-link {
  position: relative;
  transition: all 0.3s ease;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: hsl(var(--primary));
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}
</style>
