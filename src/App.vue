<template>
    <transition-group name="slideContainer" mode="out-in">
        <component key="mainComponent" :is="activeComponent" @activeComponentEvent="activeComponent = $event">
        </component>
        <canvas key="canvas" id="canvas" v-show="activeComponent == 'app-celebrate'"></canvas>
    </transition-group>
</template>
<script>
import GameCards from './components/GameCards.vue'
import Celebrate from './components/Celebrate.vue'
import Failure from './components/Failure.vue'


export default {
    data() {
        return {
            activeComponent : "app-game-cards"
        }
    },
    components: {
       appGameCards: GameCards,
       appCelebrate : Celebrate,
       appFailure: Failure
    }
}
</script>
<style>
    body {
        font-family: sans-serif;        
    }

    .slideContainer-enter{}
    .slideContainer-enter-active{
        animation: slide-in 1 ease-out forwards;
    }

    .slideContainer-leave{}
    .slideContainer-leave-active{
          animation: slide-out 1 ease-out forwards;
    }

    @keyframes slide-in {
        from {
            transform: translateX(-1000px);
        }

        to {
            transform: translateX(0); 
        }
    }

        @keyframes slide-out {
        from {
            transform: translateX(0);
        }

        to {
            transform: translateX(1000px); 
        }
    }

</style>
