<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Tasks Management</div>
                    <div v-for="(task,index) in tasks" :key="index">
                        <TaskBody v-bind:task="task" v-on:completeToggleEvent="completeToggleFun(task)"
                                  v-on:deleteTaskEvent="deleteTaskFun(index)"></TaskBody>
                    </div>
                    <div class="p-1">
                        <input class="mb-2 container-fluid form-control" v-model="taskText" placeholder="ADD NEW TASK">
                        <button class="form-control btn btn-success container-fluid" @click.prevent="addTask">Add Task
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import TaskBody from './TaskBody'

    export default {
        data() {
            return {
                tasks: [
                    {
                        'body': 'feras', 'complete': false
                    },
                    {
                        'body': 'moh', 'complete': false
                    },
                    {
                        'body': 'ahme', 'complete': false
                    },
                    {
                        'body': 'os', 'complete': false
                    },
                ],
                taskText: null
            }
        }, components: {
            TaskBody,
        },
        methods: {
            completeToggleFun(task) {
                task.complete = !task.complete;
            },
            deleteTaskFun(id) {
                this.tasks.splice(id, 1)
            },
            addTask() {
                this.tasks.push({'body': this.taskText, 'complete': false});
                this.taskText = null;
            }
        }
    }
</script>
<style scoped>

    .list-group-item {
        display: flex;
        justify-content: space-between;
    }
</style>