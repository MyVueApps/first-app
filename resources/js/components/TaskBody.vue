<template>
    <div class="card">
        <div class="card-body ">
            <ul class="list-group">
                <li class="list-group-item">
                    <div v-bind:class="{complete:this.task.complete}">{{this.task.body}}</div>
                    <div class="icons">
                        <i class="fa fa-check" @click="completeToggle(task)"></i>
                        <i class="fa fa-trash ml-3" @click="deleteTask  "></i>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['task'],
        methods: {
            completeToggle (task) {
                this.$emit('completeToggleEvent',task);
            },deleteTask () {
                this.$emit('deleteTaskEvent');
            }
        }
    }
</script>

<style scoped>
    .complete {
        color: green;
        text-decoration: line-through;
    }

    .list-group-item {
        display: flex;
        justify-content: space-between;
    }
</style>