<template>
    <section>
        <transition-group name="list" tag="ul"> <!-- animation tag -->
            <li v-for="(item,index) in listData" v-bind:key="item" class="shadow">
                <span class="updateBtn" type="button" @click="updateTodo(index)">
                    <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                </span>    
                <span class="content"> &nbsp; {{ item }}</span>
                <input class="inputBox content-input" v-model="updateData" placeholder="insert content to update" v-on:keyup.enter="updateData"/>
                <i class="closeModalBtn fas fa-times " aria-hidden="true" v-on:click="cancelModify(index)"></i>
                <span class="removeBtn" type="button" @click="removeTodo(item, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>

<script>
    export default {
        props: [
            'listData',
        ],
        data() {
            return {
                updateData: [],
            };
        },

        methods: {
            removeTodo(item, index) {
                confirm("삭제하시겠습니까?") 
                    this.$emit('removeEvent', item, index);
                    alert("삭제되었습니다.");    
            },
            updateTodo(index) { //To do :: 변수선언 후 버튼하나로 분기처리
                document.querySelectorAll(`.content`)[index].style.display='none';
                document.querySelectorAll(`.content-input`)[index].style.display='block';
                document.querySelectorAll(`.closeModalBtn`)[index].style.display='block';
            },
            cancelModify(index) {
                document.querySelectorAll(`.content`)[index].style.display='block';
                document.querySelectorAll(`.content-input`)[index].style.display='none';
                document.querySelectorAll(`.closeModalBtn`)[index].style.display='none';
            },
        }
            
            // updateData(item, index) {

            // }
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
        cursor: pointer;
    }

    .updateBtn {
        cursor: pointer;
    }

    .list-enter-active, .list-leave-active {
        transition: all 1.5s;
    }

    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }

    .inputBox {
        border-radius: 5px;
        border-style: none;
        margin-left: 10px;
        height: 25px;
        background: linear-gradient(to left, white, lightgray);
        color:black;
        margin-top: 20px;
    }

    .content-input {
        display: none;
    }

    .closeModalBtn {
        margin-top: 27px;
        margin-left: 10px;
        display: none;
        cursor: pointer;
    }
</style>