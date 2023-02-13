<template>
  <div class="w-screen h-screen bg-gray-300 p-7">
    <h1 style="font-size: 3em">Voice QL Console</h1>
    <command-list />
    <chat-widget />
  </div>
</template>

<script lang="ts">
import ChatWidget from '@/components/ChatWidget.vue';
import CommandList from '@/components/CommandList.vue';
import { Component, Vue } from 'vue-property-decorator';

@Component({
  components: { ChatWidget, CommandList },
})
export default class App extends Vue {}
</script>

<style>
@import 'assets/css/theme.pcss';

#app {
  -webkit-tap-highlight-color: transparent;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
