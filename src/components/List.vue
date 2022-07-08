<template>
    <section>
        <ul>
            <li v-for="(item,index) in listData" v-bind:key="item" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                    &nbsp; {{ item }}
                <span class="removeBtn" type="button" @click="removeTodo(item, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
    export default {
        props: [
            'listData',
        ],
        data() {
            return {
                
            };
        },
        methods: {
            removeTodo(item, index) {
                this.$emit('removeEvent', item, index);
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 10;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 70px;
        height: 50px;
        line-height: 70px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 10px;
    }

    .checkBtn {
        line-height: 65px;
        color: #62acde;
        margin-left: 5px;
    }

    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>