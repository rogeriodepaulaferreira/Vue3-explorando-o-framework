<template>
    <section>
        <strong>
            {{ elapsedTime }}
        </strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'

    export default defineComponent({
        name: 'TaskTimer',
        props: {
            timeElapsed : {
                type: Number,
                default: 0
            }
        },
        computed:{
            elapsedTime () : string {
                return new Date(this.timeElapsed * 1000).toISOString().substr(11,8);
            }
        },
    });

</script>