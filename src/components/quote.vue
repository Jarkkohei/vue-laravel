<template>
    <div class="card mb-4">
        <div class="card-body">
            {{ qt.content }}
        </div>

        <div class="card-footer">
            <div v-if="editing">
                <input type="text" v-model="editValue">
                <a @click="onUpdate">Save</a>
                <a @click="onCancel">Cancel</a>
            </div>

            <div v-if="!editing">
                <a @click="onEdit">Edit</a>
                <a @click="onDelete">Delete</a>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        props: ['qt'],
        data() {
            return {
                editing: false,
                editValue: this.qt.content
            }
        },
        methods: {
            onEdit() {
               this.editing = true,
               this.editValue = this.qt.content
            },
            onCancel() {
                this.editing = false
            },
            onUpdate() {
                this.editing = false;
                this.qt.content = this.editValue;
                axios.put('http://localhost:8000/api/quote/' + this.qt.id, { content: this.editValue })
                    .then(response => console.log(response))
                    .catch(error => console.log(error));
            },
            onDelete() {
                this.$emit('quoteDeleted', this.qt.id);
                axios.delete('http://localhost:8000/api/quote/' + this.qt.id)
                    .then(response => console.log(response))
                    .catch(error => console.log(error));
            }
        }
    }

</script>

<style scoped>
    a {
        cursor: pointer;
    }
</style>