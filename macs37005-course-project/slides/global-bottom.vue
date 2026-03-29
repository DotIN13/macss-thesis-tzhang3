<template>
  <footer
    v-if="$slidev.nav.currentLayout !== 'cover' && $slidev.nav.currentLayout !== 'intro'"
    class="absolute bottom-4 right-4 text-sm text-gray-500 opacity-50 font-sans"
  >
    {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
  </footer>
</template>
