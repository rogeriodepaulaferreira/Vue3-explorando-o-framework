<template> 
    <main class="columns is-gapless is-multiline" :class="{'dark-mode' : darkMode}">
        <div class="column is-one-quarter">
            <SideBar @onSwitchTheme="switchTheme" />
        </div>
        <div class="column is-three-quarter content">
            <FormTasks @onSubmit="saveTask" />
            <div class="lista">
                <Tasks v-for="(task, index) in tasks" :key="index" :task="task" />
                <TaskBox v-if="emptyTasks">
                    Nenhuma tarefa adicionada até o momento
                </TaskBox>
            </div> 
        </div>
    </main>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import SideBar from './components/SideBar.vue';
    import FormTasks from './components/FormTasks.vue';
    import Tasks from './components/Tasks.vue'; 
    import ITask from './interfaces/ITask.js';
import TaskBox from './components/TaskBox.vue';

    export default defineComponent({
    name: "App",
    components: {
    SideBar,
    FormTasks,
    Tasks,
    TaskBox
},
    data(){
        return {
            tasks: [] as ITask[],
            darkMode: false
        }
    },
    computed:{
        emptyTasks() : boolean{
            return this.tasks.length === 0;
        }
    },
    methods: {
        saveTask(task:ITask){
            this.tasks.push(task)
        }, switchTheme(darkMode: boolean) {
            this.darkMode = darkMode
        }
    }
});
</script>
<style>
    .lista{
        padding: 1.25rem;
    }
    main{
        --default-background:#FFF;
        --default-text:#000;
    }
    main.dark-mode{
        --default-background:#2b2d42;
        --default-text:#ddd;
    }
    .content{
        background-color: var(--default-background);
    }
</style>