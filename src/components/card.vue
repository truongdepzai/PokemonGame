<template>
    <div class="card">
        <div class="card-inner" :class="{'is-flipped' :isFlipped},`card-${card.index}`" @click="onToggleFlipCard()" >
            <div class="card-face card-face-front">
                <div class="card-content"></div>
            </div>
            <div class="card-face card-face-back">
                <img alt="" class="card-content" :src="`src/assets/image/${imgBackFaceUrl}.png`"  >

            </div>
        </div>
    </div>
</template>

<script>


    export default{
        name: 'card',
        data() {
            return {
                isFlipped: false,
            };
        },
        methods: {
            onToggleFlipCard() {
                this.isFlipped = !this.isFlipped;
                if (this.isFlipped){
                    this.$emit("onFlip",this.card);
                }
       
            },
            flipBackCard() {
                this.isFlipped = false;
            },
        },
        props: {
            imgBackFaceUrl: {
                type: String,
                required: true,
            },
            card:{
                type: [String,Number, Array,Object],

            }
          
        },

    }
</script>

<style lang="css" scoped>
    .card{
        display: inline-block;
        margin-right: 1rem;
        margin-bottom: 1rem;
        width: 90px;
        height: 120px;
    }

    .card-inner{
        width: 100%;
        height: 100%;
        transition: transform 1s;
        transform-style: preserve-3d;
        cursor: pointer;
        position: relative;
    }

    .card-inner.is-flipped{
        transform: rotateY(-180deg);
    }

    .card-face{
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
        overflow: hidden;
        border-radius: 1rem;
        padding: 1rem;
        box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.2);
    }

    .card-face-front .card-content{
        background: url("../assets/image/icon_back.png") no-repeat center center;
        background-size: 60px 60px;
        height: 100%;
        width: 100%;
    }
    .card-face-back{
        background-color: var(--light);
        transform: rotateY(-180deg);
    }

    .card-face-back .card-content{

        background-size: contain;
        background-position: center center;
        background-repeat: no-repeat;
        height: 100%;
        width: 100%;
    }
</style>