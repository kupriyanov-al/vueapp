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
    <app-note v-for="note in notes" :key="note.id" :head="note.head" :desc="note.desc" :id="note.id" :is-open="note.isOpen"></app-note>

  </div>


</template>


<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import AppNote from './components/AppNote.vue';

export default {
 
  data() {
    return {
      openRate: 0,
      newNote: {
        id: 0,
        head: '',
        desc: '',
        isOpen: false
      },
      
      notes: [{
        id: 1,
        head: "Заголовок1",
        desc: "Описание1",
        isOpen: false
      },
      {
        id: 2,
        head: "Заголовок2",
        desc: "Описание3",
        isOpen: false
      }
      ]
    }
  },
  methods: {
    newAddNote() {
      this.newNote.id=this.notes.length+1
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
