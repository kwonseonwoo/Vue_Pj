<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" @keyup.enter="addTodo">
        <span class="addContainer" @click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                newTodoItem: '',
            }
        },
        methods: {
            addTodo() {
                // console.log(`this input data: ${this.newTodoItem}`);
                if(this.newTodoItem != "") {
                    let val = this.newTodoItem && this.newTodoItem.trim();
                    this.$emit('inputData', val);
                    this.clearInput();
                }
            },
            clearInput() {
                this.newTodoItem = '';
            },
        }
    }
</script>

<style scoped>
    input:focus {
        outline: none;
    }

    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }

    .inputBox input {
        border-style: none;
        font-size: 1.0rem;
    }

    .addContainer {
        float:right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
        cursor: pointer;
    }

    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>