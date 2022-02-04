<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}
            <i @click="onDelete(task.id)">x</i>
        </h3>
        
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods : {
        onDelete(id) {
            this.$emit('delete-task', id)
            // console.log(id)
        }
    }
}
</script>

<style scope>
    i {
        color: red;
    }
    .task {
        background: #d4d4d4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
        border-radius: 20px;
    }

    .task.reminder {
        border-left: 10px solid green;
    }

    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>