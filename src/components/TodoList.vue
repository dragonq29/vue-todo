<template>
    <section>
        <ul>
            <li class="shadow" v-for="(todoItem, index) in todoItems" v-bind:key="todoItem">
                <i class="checkBtn fa fa-check" aria-hidden="ture"></i>
                {{todoItem}}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                <!-- <span class="removeBtn" type="button" @click="removeTodo"> -->
                    <i class="fa fa-trash-alt" aria-hidden="true"></i>
                </span>
                </li>
        </ul>
    </section>
</template>

<script>
export default {
    data() {
        return {
            todoItems: []
        }
    },
    created() {
        if (localStorage.length > 0) {
            for (let i = 0; i < localStorage.length; i++) {
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    methods: {
        removeTodo(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1)
        }
    }
}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }
    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }
    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>