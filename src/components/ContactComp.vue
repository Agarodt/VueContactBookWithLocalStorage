<template>
<div class='card'>
    <p>Name: {{firstName}} <input v-show='visible' v-model='newName' placeholder='New name'/></p>
    <p>Email: {{email}} <input v-show='visible' v-model='newEmail' placeholder='New email'/></p>
    <button v-show='editOff' @click="visible=true, editOff=false">edit</button>
    <button v-show='visible' @click="sendNew">save</button>
    <button @click="$emit('on-delete')">delete</button>
    </div>
</template>
<script>


export default {
    data(){
        return{
            visble: false,
            editOff: true
        }
    },

    props:{
        firstName: String,
        email: String,
    },
    methods:
    {
        sendNew(){
            this.$emit('on-save',[this.newName, this.newEmail])
            this.visible=false
            this.editOff=true
        }
    }
}
</script>
<style scoped>
.card{
    width: 320px;
    margin-top: 3px;
    margin-bottom: 3px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid black
}
</style>
