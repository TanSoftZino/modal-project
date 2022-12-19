<template>
  <h1>{{ hello }} </h1> <br/>
  <button @click="toggleModal" style="margin: 20px">Open Modal</button> 
  <button @click="toggleModal2" style="margin: 20px">Show Modal 2</button><br/>
  <input type="text" ref="name">
  <button @click="handleClick" style="margin: 5px">Click here!</button>
  <Teleport to=".modals" v-if="showModal">
    <Modal :someArray="['value', 4]"  :value="40" text="some text" @close="toggleModal">
    <template v-slot:links>
       <a href="www.google.com">Sign up Now!</a>
       <a href="www.google.com">Login in!</a>
    </template>
    <p>Did you know that You can do MUCH MORE when you sign in!</p> 
    </Modal>
  </Teleport>
  <div v-if="showModal2">
    <Modal @close="toggleModal2">
        <p>Some random quotes!</p>
    </Modal>

  </div>
</template>

<script>
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  data() {
    return {
      hello : "Hello there!",
      showModal: false,
      showModal2: false,
    };
  },
  components: {
    Modal
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    handleClick() {
    console.log(this.$refs.name);
    this.$refs.name.classList.add("active");
    this.$refs.name.focus();
  },
  toggleModal2() {
    this.showModal2 = !this.showModal2;
  },
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
h1 {
  border-bottom : 1px solid blue;
  display : inline-block;
  padding-bottom: 10px;
}
a{
  padding:5px;
  margin:10px;
  background: lightgrey;
  border-radius: 10px;

}
</style>
