<template>
  <div class="change-page">
    <AddNote @add-note="addNote" />
    <Note v-if="addnote" :title="curNote" @close="closeNote"/>
  </div>
</template>

<script>
import AddNote from '../components/AddNote.vue'
import Note from '../components/Notes.vue'
// import axios from 'axios'
export default {
  name: 'ChangePage',
  components: {
    AddNote,
    Note
  },
  data() {
    return {
      addnote: false,
      notes: [],
      curNote: ''
    }
  },
  methods: {
    closeNote() {
      this.addnote = false
    },
    addNote(newNote) {
      const { title } = newNote;
      this.addnote = true
      this.notes.push(title)
      this.curNote = title
      // axios.post('https://jsonplaceholder.typicode.com/todos', {
      //   title
      // })
      //   .then(res => {
          
      //     this.notes = [...this.notes, res.data]
      //     })
      //   .catch(err => console.log(err));
    }
  }
}
</script>

<style scoped>
  .change-page {
    width: 100%;
    height: 670px;
    background: #46d6ff;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>