<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" @keyup.enter="addTodo">
        <span class="addContainer" @click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal v-if="showModal" v-bind:show="showModal" @close="showModal = false">
            <h3 slot="header">warning</h3> <!-- modal header -->
            <!-- modal footer -->
            <span slot="footer" @click="showModal = false">
                insert works into the input box!
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>

<script>
    import Modal from './common/Modal.vue';

    export default {
        data() {
            return {
                newTodoItem: '',
                showModal: false,
            }
        },
        methods: {
            addTodo() {
                // console.log(`this input data: ${this.newTodoItem}`);
                if(this.newTodoItem != "") {
                    let val = this.newTodoItem && this.newTodoItem.trim();
                    this.$emit('inputData', val);
                    this.clearInput();
                }else {
                    this.showModal = !this.showModal;
                    console.log("log");
                    console.log(this.showModal);
                }
            },
            clearInput() {
                this.newTodoItem = '';
            },
        },
        components: {
            modal: Modal,
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