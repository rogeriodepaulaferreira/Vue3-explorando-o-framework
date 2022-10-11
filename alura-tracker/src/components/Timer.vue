<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TaskTimer :timeElapsed="timeElapsed" />
        <button class="button" @click="start" :disabled="running">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="stop" :disabled="!running">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div> 
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import TaskTimer from './TaskTimer.vue';

    export default defineComponent({
    name: "Timer",
    emits:['whenFinished'],
    components: { TaskTimer },
    data() {
        return {
            timeElapsed: 0,
            stopwatch: 0,
            running: false
        };
    },
    methods: {
        start() {
            if(!this.running){
                this.running = true;
                this.stopwatch = setInterval(() => {
                    this.timeElapsed++;
                }, 1000);
            }
        },
        stop() {
            if(this.running){
                this.running = false;
                clearInterval(this.stopwatch);
                this.$emit('whenFinished',this.timeElapsed);
                this.timeElapsed = 0;
            }
        }
    }
    
});    
</script>