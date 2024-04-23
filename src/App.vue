<script setup>
import { ref } from "vue";

// 1
const count = ref(0);
const msg = ref("Hello World");

// 2
const redTextClass = ref("red");
const greenTextId = ref("green");

// 3
const increment = () => {
  count.value++;
};

// 4
const text = ref("");
const onInput = (e) => {
  text.value = e.target.value;
};

// 5
const awesome = ref(true);
const toggle = () => {
  awesome.value = !awesome.value;
};

// 6
let id = 0;
const newTodo = ref("");
const todos = ref([
  {
    id: id++,
    text: "Hello World",
  },
  {
    id: id++,
    text: "Hallo Dunia",
  },
  {
    id: id++,
    text: "America ya, Hallo :D",
  },
]);

const addTodo = () => {
  todos.value.push({
    id: id++,
    text: newTodo.value,
  });
  newTodo.value = "";
};

const removeTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};
</script>

<template>
  <div class="container">
    <div class="container-fluid m-5">
      <section class="mb-3">
        <h1 class="text-primary">Declarative Rendering</h1>
        <div class="d-flex">
          <p class="text-dark">
            Counter : <span class="text-danger"> {{ count }} </span>
          </p>
        </div>
        <div>
          <p>
            Split reverse join dari {{ msg }} menjadi :
            <span class="text-danger">
              {{ msg.split("").reverse().join("") }}
            </span>
          </p>
        </div>
        <button @click="count++" class="btn btn-primary">Klik saya</button>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">Attribute Binding</h1>
        <p :class="redTextClass">Red class dari {{ redTextClass }}</p>
        <p :id="greenTextId">Green ID dari {{ greenTextId }}</p>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">Event Listeners</h1>
        <p class="text-dark">
          Di eksekusi dengan func :
          <span class="text-primary"> {{ count }}</span>
        </p>
        <button @click="increment" class="btn btn-primary">Klik saya</button>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">Form Bindings</h1>
        <div class="py-2">
          <div class="d-flex align-items-center gap-2">
            <p class="d-flex m-0">Ketik disini text :</p>
            <input :value="text" @input="onInput" placeholder="Type here" />
          </div>
          <p class="py-2">Output : {{ text }}</p>
        </div>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">Conditional Rendering</h1>
        <div class="py-2 d-flex align-items-center gap-2">
          <button @click="toggle" class="btn btn-primary">Toggle</button>
          <p class="text-dark d-flex m-0">Toggle bernilai : {{ awesome }}</p>
        </div>
        <div class="text-dark py-3">
          <p v-if="awesome">Vue sangat mantap</p>
          <p v-else>Oh no sadge</p>
        </div>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">List Rendering</h1>
        <div class="py-2">
          <form @submit.prevent="addTodo" class="d-flex">
            <input v-model="newTodo" required placeholder="new todo" />
            <button class="btn btn-primary rounded-0">Add Todo</button>
          </form>
        </div>
        <ul>
          <li v-for="todo in todos" :key="todo.id" class="py-2">
            {{ todo.text }}
            <button @click="removeTodo(todo)" class="btn btn-danger m-0 p-2">
              X
            </button>
          </li>
        </ul>
      </section>
      <section class="mb-3">
        <h1 class="text-primary">List Rendering</h1>
        <div class="py-2">
          <form @submit.prevent="addTodo" class="d-flex">
            <input v-model="newTodo" required placeholder="new todo" />
            <button class="btn btn-primary rounded-0">Add Todo</button>
          </form>
        </div>
        <ul>
          <li v-for="todo in todos" :key="todo.id" class="py-2">
            {{ todo.text }}
            <button @click="removeTodo(todo)" class="btn btn-danger m-0 p-2">
              X
            </button>
          </li>
        </ul>
      </section>
    </div>
  </div>
</template>

<style scoped>
.red {
  color: red;
}

#green {
  color: green;
}
</style>
