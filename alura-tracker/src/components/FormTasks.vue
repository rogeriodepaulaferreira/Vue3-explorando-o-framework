<template>
    <div class="box task-form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description">
            </div>
            <div class="column">
                <Timer @whenFinished="saveTask" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Timer from './Timer.vue'; 

    export default defineComponent({
    name: "FormTasks",
    emits:['onSubmit'],
    components: { 
        Timer 
    }, 
    data(){
        return {
            description:''
        }
    },
    methods: {
        saveTask(elapsedTime:number) :void{
            this.$emit('onSubmit',{
                time: elapsedTime,
                description: this.description 
            })
            this.description = ''
        }
    }
});    
</script>
<style>
    .task-form {
        color: var(--default-text);
        background-color: var(--default-background);
    }
</style>