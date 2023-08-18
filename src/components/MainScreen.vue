<template>
    <div class="screen items-center jusitfy-center">
        <h1 class="text-4xl font-bold mb-10 text-white"> POKEMON GAME</h1>
        <h3 class="mb-5 text-3xl font-bold text-white">Select mode to start game</h3>
        <div class="actions grid grid-cols-4 gap-4 h-20">
            <button class="bg-black border-white border-2 rounded hover:bg-green-500" @click="onStart(16)">
                <span >4x4</span>
                <span >Easy</span>
            </button>
            <button class="bg-black border-white border-2 rounded hover:bg-green-500" @click="onStart(36)">
                <span>6x6</span>
                <span>Normal</span>
            </button>
            <button class="bg-black border-white border-2 rounded hover:bg-green-500" @click="onStart(64)">
                <span>8x8</span>
                <span>Hard</span>
            </button>
            <button class="bg-black border-white border-2 rounded hover:bg-green-500" @click="onStart(100)">
                <span>10x10</span>
                <span>Super Hard</span>
            </button>
        </div>
    </div>
</template>

<style>
    span{
        color:white
    }
</style>


<script >
export default{
    name: 'MainScreen',
    methods: {
        onStart(totalOfBlocks){
            this.$emit("onStart",{totalOfBlocks});
        }
    },
}


  
</script>
