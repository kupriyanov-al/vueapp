<template>
  <div class="header">
    <div class="card mb-3">
      <div class="card-body">
        Список заметок <span class="badge bg-secondary">{{ notes.length }}</span>
      </div>
      
    </div>
    <div class="card mb-3">
      <div class="card-body">
        <div class="mb-3">
          <label for="exampleFormControlInput1" class="form-label">Введите текст заголовка</label>
          <input type="text" class="form-control" id="exampleFormControlInput1" placeholder="Заголовок"
            v-model="newNote.head">
          <label for="exampleFormControlInput2" class="form-label">Описание</label>
          <input type="text" class="form-control" id="exampleFormControlInput2" placeholder="Описание"
            v-model="newNote.desc">
          <button type="button" class="btn btn-outline-primary mt-3" @click="newAddNote">Добавить</button>
        </div>
      </div>
    </div>
    <!-- Карточка для заполнения -->
    <app-note v-for="(note, index) in notes" :key="index" :head="note.head" :desc="note.desc"></app-note>

  </div>


</template>


<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import AppNote from './components/AppNote.vue';

export default {
 
  data() {
    return {
      
      newNote: {

        head: '',
        desc: ''
      },
      
      notes: [{

        head: "Заголовок1",
        desc: "Описание1"
      },
      {

        head: "Заголовок2",
        desc: "Описание3"
      }
      ]
    }
  },
  methods: {
    newAddNote() {
      this.notes.push(Object.assign({}, this.newNote))
      this.newNote.desc = ''
      this.newNote.head = ''
    },

    delNote(index) {
      this.notes.splice(index, 1)
    }
  },
  components: {'app-note':AppNote}
}
</script>




<style scoped>
.header {
  width: 800px;


}
</style>
