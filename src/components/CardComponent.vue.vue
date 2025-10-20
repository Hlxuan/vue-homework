<template>
  <div>
    <header>
      <slot name="cardHeader"></slot>
    </header>
    <main>
      <slot></slot>
    </main>
    <footer>
      <slot name="cardFooter"></slot>
    </footer>
  </div>
</template>

<style scoped></style>

<script setup></script>
