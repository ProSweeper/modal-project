<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <!-- if the following is not present the default slot will render -->
      <h1>GiveAway</h1>
      <p>come get it obama</p>
    </Modal> 
  </teleport>

  <teleport to=".modals" v-if="showModal2">
    <Modal @close="toggleModal2">
      <template v-slot:links>
        <a href="#">sign up again</a>
        <a href="#">more info on stuff</a>
      </template>
      <!-- if the following is not present the default slot will render -->
      <h1>YEYE</h1>
      <p>what it doooooo</p>
    </Modal> 
  </teleport>
  
  <button @click="handleClick">click me</button>
  <br>
  <button @click.alt="toggleModal">Toggle Modal (alt)</button>
  <button @click.alt="toggleModal2">Toggle Modal 2 (alt)</button>
</template>

<script>
import Modal from "./components/ModalComp.vue"

export default {
  name: 'App',
  data() {
    return {
      title: "My First Vue App",
      header: "Hello There",
      string: "heeyyyoooo",
      showModal: false,
      showModal2: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2
    }
  },
  components: {
    Modal,
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
