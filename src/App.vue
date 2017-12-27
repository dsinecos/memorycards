<template>
  
  <div class="row">
    <div class="col-xs-8 col-xs-offset-2">
      <memorycards-instructions></memorycards-instructions>
      <memorycards-settings></memorycards-settings>
      <memorycards-stats></memorycards-stats>
      <!-- <memorycards-setup></memorycards-setup> -->
      <!-- <memorycards-statistics></memorycards-statistics> -->
      <memorycards-board></memorycards-board>
    </div>
  </div>

</template>

<script>
  // import gameSetup from './components/gameSetup.vue';
  // import gameStatistics from './components/gameStatistics.vue';
  import gameBoard from './components/gameBoard.vue';
  import gameInstructions from './components/gameInstructions.vue';
  import gameSettings from './components/gameSettings.vue';
  import gameStats from './components/gameStats.vue';

  export default {
    components: {
      // 'MemorycardsSetup': gameSetup,
      // 'MemorycardsStatistics': gameStatistics,
      'MemorycardsBoard': gameBoard,
      'MemorycardsInstructions': gameInstructions,
      'MemorycardsSettings': gameSettings,
      'MemorycardsStats': gameStats
    }

  }

</script>

<style>

</style>