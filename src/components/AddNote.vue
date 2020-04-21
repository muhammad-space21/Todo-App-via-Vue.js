<template>
  <div class="add-note-container">
    <form @submit.prevent="addNote">
      <input type="text" v-model="title" name="title" placeholder="Add Note...">
      <input type="submit" value="Add Note" class="button-add">
    </form>
  </div>
</template>

<script>
export default {
  name: 'AddNote',
  methods: {
    addNote() {
      const newNote = {
        title: this.title
      }
      // Send up to parent
      this.$emit('add-note', newNote);
      this.title = '';
    }
  }
}
</script>

<style scoped>
  .add-note-container {
    width: 80%;
    height: fit-content;
    margin-top: 50px;
  }
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
    margin-left: 20px;
    margin-right: 20px;
    background: #46D6FF;
    border: none;
    border-bottom: 2px solid #2DCC70;
    color: white;
  }
</style>