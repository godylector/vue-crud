<template>
    <div>
        <h1>สร้างโปรไฟล์ใหม่</h1>
        <task-form @createOrUpdate="createOrUpdate"></task-form>
    </div>
</template>

<script>
    import taskForm from '../components/TaskForm.vue'
    import { api } from '../helpers/Helpers'

    export default {
        name: "new-task",
        components: {
            'task-form': taskForm,
        },
        methods: {
            createOrUpdate: async function(task){
                const res = await api.createtask(task);
                const message = "สร้างโปรไฟล์ของ '" + task.task1 + "' สำเร็จ";
                this.flash(message, 'success');
                this.$router.push(`/tasks/${res._id}`);
            }
        }
    }
</script>