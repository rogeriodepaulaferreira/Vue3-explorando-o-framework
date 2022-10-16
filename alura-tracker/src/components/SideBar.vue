<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="switchTheme">
            {{ descriptionButtonTheme }}
        </button>
    </header>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent( {
        name:'SideBar',
        emits:['onSwitchTheme'],
        data(){
            return {
                darkMode:false
            }
        },
        computed: {
            descriptionButtonTheme() {
                if(this.darkMode){
                    return 'Desativar modo escuro';
                }
                return 'Modo escuro';
            }
        },
        methods:{
            switchTheme() { 
                this.darkMode = !this.darkMode
                this.$emit('onSwitchTheme',this.darkMode)
            }
        }
    });
</script>

<style scoped>
    header {
        padding: 1rem;
        background: #0d3b66;
        width: 100%;
        height: 100vh;
        text-align: center;
    }
    @media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
    }
</style>