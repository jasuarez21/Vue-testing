<template>
    <div>
        <p>{{text}}</p>
        <ul>
            <li v-for="toDo in toDoList" :key="toDo.sentence" v-bind:class="[toDo.done === true ? activeClass : 'done', errorClass]">
                {{ toDo.sentence }}
                <button v-on:click="doneFunction(toDo)">Done</button>
                <button v-on:click="deleteFunction(toDo)">Borrar</button>
            </li>
        </ul>
         <button v-on:click="addTodo">Añadir</button>
    </div>
</template>

<script>
export default {
  name: 'BodyComponent',
  data(){
      return {
          text: "Esta es tu To-Do List, cuándo hagas la tarea pulsa el botón 'Done', si quieres borrarla pulsa el botón 'Borrar'y si deseas otra tarea pulsa el botón 'Añadir'",
          toDoList: [{
            done: false,
            sentence: "Comprar leche"
          },
          {
            done: false,
            sentence: "Ir al recoger el coche al taller"
          },
          {
            done: false,
            sentence: "Hacer los deberes"
          }
          ],
      }
  },
  methods: {
      doneFunction: function(doneTodo){
          this.toDoList.map(toDo => {
              if(toDo.sentence === doneTodo.sentence){
                  toDo.done = !toDo.done
              }
          })
      },
      deleteFunction: function(deleteTodo){
          this.toDoList = this.toDoList.filter(toDo => toDo.sentence !== deleteTodo.sentence)
      },
      addTodo: function(){
          let toDotoAdd = prompt("Que toDo quieres añadir?")
          this.toDoList.push({done: false, sentence: toDotoAdd})
      }
  }
}
</script>

<style scoped>
ul {
    list-style: none;
}
.done {
    text-decoration: line-through;
    color: green;
    font-style: italic;
}
.notDone{
    color: 'black'
}
</style>
