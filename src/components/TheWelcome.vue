<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue';
import DocumentationIcon from './icons/IconDocumentation.vue';
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Tweet AI</template>

   Hello, I am Ndubuisi Ollawa
    <a href="https://github.com/ndollawa/tweet-ai.git" target="_blank" rel="noopener">GitHub</a>
    provides you with all information you need to get started.
  </WelcomeItem>


 
</template>
