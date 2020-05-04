<template>
    <div class="task"  :class="stateClass">
        <span @click="$emit('taskStateChanged', task)" class="check" >&#10004;</span>
        <span @click="$emit('taskDeleted', task)" class="close">x</span>
        <p>{{ task.name }}</p>
    </div>
</template>

<script>

export default {
    props: {
        task: { type: Object, required: true }
    },
    computed: {
        stateClass(){
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    },
}
</script>

<style>

    .task {
        position: relative;
        box-sizing: border-box;   
        width: 300px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 300;        
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .pending {
        border-left: 12px solid #B73229;
        background-color: #F44336;
    }
    .done {
       color: rgba(221, 221, 221, 0.5);
       border-left: 12px solid #0A8F08;
       background-color: #4CAF50;
       text-decoration: line-through;
    }
    .pending .close {
        background-color: #b73229;
    }

    .done .close {
        background-color: #0a8f08;
    }

    .close {
        cursor: pointer;
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: .9rem;
        font-weight: 600;
        width: 20px;
        height: 20px;
        border-radius: 10px;
        display:flex;
        justify-content: center;
    }

    .close:hover{
        background-color: #6971db;
    }

    .check {
        cursor: pointer;
        position: absolute;
        left: 10px;
        top: 10px;
        font-size: .9rem; 
        width: 20px;
        height: 20px;
        border-radius: 10px;
        display:flex;
        justify-content: center; 
    }

    .pending .check {
        background-color: #b73229;
    }

    .done .check {
        background-color: #0a8f08;
    }

    .check:hover {
        background-color: #6971db;
    }
</style>