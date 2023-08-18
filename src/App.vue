<script >
import MainScreen from './components/MainScreen.vue';
import CoppyRightScreen from './components/CoppyRightScreen.vue';
import InterractScreen from './components/InterractScreen.vue';
import ResultScreen from './components/ResultScreen.vue';
import {shuffled} from "./utils/array"
  export default{
    name:' App',
    data(){
      return{
        statusMatch: 'default',
        settings: {
          totalOfBlocks: 0,
          cardsContext: [],
          startedAt: null,
        }
      }
    },
  
    components: {
      MainScreen,
      CoppyRightScreen,
      InterractScreen,
      ResultScreen
    },
    methods: {
      onHandleBeforeStart(config) {
        this.settings.totalOfBlocks = config.totalOfBlocks;

        const firstCards = Array.from({length: this.settings.totalOfBlocks /2 }, (_, i ) => i+1 );
        
        const secondCards = [...firstCards];
        const cards = [...firstCards, ...secondCards];
        
        this.settings.cardsContext = shuffled(shuffled(shuffled(cards)));
        this.settings.startedAt = new Date().getTime();

        this.statusMatch = 'match';
      }
    }
  }


</script>

<template>
  <div class="grid grid-cols-6 gap-4">
    <div class="col-start-3 col-span-2">
      <MainScreen  v-if="statusMatch==='default'" @onStart="onHandleBeforeStart($event)"/>
      <InterractScreen
         v-if="statusMatch==='match'" 
         :cardsContext="settings.cardsContext"/>
    </div>
  </div>
  
</template>