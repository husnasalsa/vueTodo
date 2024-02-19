<script>
export default{
    props:["todo","index"],
    emits:["deleteTodo","changeStatusTodo"]
}

</script>
<template>
    <div class="card m-2 py-1">
        <div class="row">
            <div class="col-6 form-check d-flex justify-content-start p-1">
                <input class="form-check-input" value="" type="checkbox" @change="$emit('changeStatusTodo',this.index)">
                <label v-if="this.todo.status === false" class="form-check-label ms-3">{{ todo.content }}</label>
                <label v-else class="form-check-label text-decoration-line-through ms-3">{{ todo.content }}</label>
            </div>
            <div class="col-4 p-1">
                <p>{{ todo.date }}</p>
            </div>
            <div class="col-2 d-flex justify-content-end">
                <button @click="$emit('deleteTodo',this.index)" class="btn btn-link">Hapus</button>
            </div>
        </div>
    </div>
    

</template>

<style scoped>
</style>