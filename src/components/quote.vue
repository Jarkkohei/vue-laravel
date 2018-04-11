<template>
    <div class="card mb-4">
        <div class="card-body">
            {{ qt.content }}
        </div>

        <div class="card-footer">
            <div>
                <input type="text">
                <a href="" @click="onUpdate">Save</a>
                <a href="" @click="onCancel">Cancel</a>
            </div>
            <div>
                <a href="" @click="onEdit">Edit</a>
                <a href="" @click="onDelete">Delete</a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['qt']
    }

</script>