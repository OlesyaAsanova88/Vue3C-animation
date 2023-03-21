<script setup>
import {ref} from "vue"

const names = ref(["Selena", "Horhe"])
const nameInput = ref("")

const addInvitee = () => {
  names.value.unshift(nameInput.value);
  nameInput.value = ""
}

const removeInvitee = (name) => {
  names.value = names.value.filter(n => n !== name)
}

</script>

<template>
  <div class="container">
    <input
     type="text" 
     placeholder="Add person..."
     v-model="nameInput"
     @keypress.enter="addInvitee"
     >
    <ul>
      <TransitionGroup name="invitees">
        <li 
        v-for="name in names" 
        :key="name"
        @click="removeInvitee(name)"
        > 
        {{ name }}
       </li>
      </TransitionGroup>
    </ul>
  </div>
</template>

<style scoped>
.container {
 max-width: 300px;
 margin: 0 auto;
}
 
.container input {
  
  margin-top: 50px;
 
  width: 100%;
  border-radius: 5px;
  border: 1px solid rgba(128, 128, 128, 0.13);
  margin-bottom: 30px;
  padding: 10px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.12);
}
ul {
  display: inline;
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
  width: 300px;
  border-radius: 5px;
  padding: 5px 10px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.12);
  text-align: center;
  cursor: pointer;
  margin-bottom: 15px;
}

.invitees-enter-from {
  opacity: 0;
  transform: scale(0.5);
}
.invitees-enter-to {
  opacity: 1;
  transform: scale(1);
}
.invitees-enter-active {
  transition: all 0.5s ease;  
}

.invitees-leave-from {
  opacity: 1;
  transform: scale(1);
}
.invitees-leave-to {
  opacity: 0;
  transform: scale(0);
}
.invitees-leave-active {
  transition: all 0.5s ease;  
  position: absolute;
}
.invitees-move {
  transition: all 0.5s ease;  
}
</style>