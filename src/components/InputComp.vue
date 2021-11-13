<template>
    <h1>Contact List</h1>
    <input v-model='nameValue' placeholder='name'/>
    <input v-model='emailValue' placeholder='email'/>
    <button @click='sendContact'>ok</button>
</template>
<script>
export default {
    data(){
        return{
            nameValue:'',
            emailValue:'',
        }
    },
    methods:{
        sendContact(){
            this.$emit('on-send', [this.nameValue, this.emailValue])
            this.nameValue = ''
            this.emailValue = ''

        }
    }
}

</script>
