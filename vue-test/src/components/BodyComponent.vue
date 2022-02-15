<template>
    <div>
        <p>{{text}}</p>
        <ul>
            <li v-for="toDo in toDoList" :key="toDo.sentence" v-bind:class="[toDo.done === false ? activeClass : 'done', errorClass]">
                {{ toDo.sentence }}
                <button v-on:click="doneFunction(toDo)" v-bind:class="[toDo.done === false ? 'buttonNotDone' : 'buttonDone', errorClass]">Done</button>
                <button v-on:click="deleteFunction(toDo)" class="buttonNotDone">Borrar</button>
            </li>
        </ul>
         <button v-on:click="addTodo" class="buttonNotDone">Añadir</button>
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
.buttonNotDone {
    border-radius: 5px;
    background:rgb(139, 199, 255);
    -moz-box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    -webkit-box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    display:inline-block;
    margin: 10px 0px 10px 10px;
    padding: 5px;
    height: 30px;
    text-decoration:none;
    transition: all 0.10s ease-in-out;
    -webkit-transition: all 0.10s ease-in-out;
    position:relative;
}
.buttonDone {
    border-radius: 5px;
    background:rgb(77, 241, 132);
    -moz-box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    -webkit-box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    box-shadow: 0px 5px 0px 0px rgb(0, 105, 202);
    display:inline-block;
    margin: 10px 0px 10px 10px;
    padding: 5px;
    height: 30px;
    text-decoration:none;
    transition: all 0.10s ease-in-out;
    -webkit-transition: all 0.10s ease-in-out;
    position:relative;
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
