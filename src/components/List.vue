<template>
    <input-comp @on-send='pushValues($event)'/>
    <contact-comp v-for='contact in contacts' 
    :key='contact.id'
    :firstName='contact.name'
    :email='contact.email'
    @on-delete='deleteFunc(contact)'
    @on-save='addNewValue(contact, $event)'/>
    
</template>
<script>
import InputComp from './InputComp.vue'
import ContactComp from './ContactComp.vue'

export default {
    components: {
        InputComp,
        ContactComp,
    },
    data(){
        return{
            contacts:[]
        }
    },
    mounted(){
if (localStorage.getItem('contacts')) {
    this.contacts=JSON.parse(localStorage.getItem('contacts'))
}
    },
    methods: {
        pushValues(value){
            this.contacts.push({name: value[0], email: value[1]})
            this.saveContacts()
        },
        deleteFunc(wrongValue){
            this.contacts=this.contacts.filter(contact=>contact!==wrongValue)
            this.saveContacts()
        },
        addNewValue(contact,newValue){
            contact.name=newValue[0]
            contact.email=newValue[1]
            this.saveContacts()
        },
        saveContacts(){
            let parsed = JSON.stringify(this.contacts)
            localStorage.setItem('contacts',parsed)
        }
    }
}
</script>
