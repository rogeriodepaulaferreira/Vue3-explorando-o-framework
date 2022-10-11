<template>
    <TaskBox>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <TaskTimer :timeElapsed="task.time" />
            </div>
        </div>
    </TaskBox>
</template>
<script lang="ts">
    import { defineComponent, PropType } from 'vue';
    import TaskTimer from './TaskTimer.vue';
    import ITask from '../interfaces/ITask.js';
    import TaskBox from './TaskBox.vue';
    
    export default defineComponent({
        name: 'Task',
        components: { TaskTimer, TaskBox },
        props:{
            task:{
                type: Object as PropType<ITask>,
                required:true
            }
        }
    });
</script> 