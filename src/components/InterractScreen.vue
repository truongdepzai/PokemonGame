<template>
    <div class="screen">
        <cardFlip 
            v-for="(card,index) in cardsContext" 
            :key="index" 
            :ref='`${index}`'
            :imgBackFaceUrl="`${card}`"
            :card=" { index, value: card}"
            @onFlip="checkRule($event)"
        
        />
    </div>
</template>

<script >
import { ref } from 'vue'
import cardFlip from './card.vue';
export default{
  watch: {
  },
    data(){
        return{
            rules: [],
        };
    },
    props: {
        cardsContext: {
            type: Array,
            default: function(){
                return [];
            }
        }
        

    },
    name: 'InterractScreen',
    components: {
        cardFlip,
     
    },
    methods: {
        checkRule(card) {
    
            if(this.rules.length === 2) return false;
            this.rules.push(card);

            if(this.rules.length === 2 && this.rules[0].value === this.rules[1].value){
                console.log('right...')

            } else if(this.rules.length === 2 && this.rules[0].value !== this.rules[1].value){
                 this.$refs[`${this.rules[0].index}`].this.flipBackCard();
                // this.$refs[`card-${this.rules[1].index}`].

                

                this.rules = []
                console.log('false...')
            }
            else{
                return false
            }
            

        },
        checkFlip(){
            // this.isFlipped = flase;
        }
    }
}


  
</script>