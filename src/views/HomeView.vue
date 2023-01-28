<template>
   <div class="home-page">
      <h3 class="title">{{ title }}</h3>
      <div class="container">
         <NotesForm @emitOnSubmit="handleSubmit" />
         <template v-if="notes.length">
            <NotesList :items="notes" />
         </template>
         <template v-else>
            <p class="empty">Заметок пока нет</p>
         </template>
      </div>
   </div>
</template>

<script>
import NotesForm from "@/components/NotesForm";
import NotesList from "@/components/NotesList";

export default {
   name: "HomeView",
   components: {
      NotesForm,
      NotesList,
   },
   data: () => ({
      title: 'Заметки',
      notes: [],
   }),
   mounted() {
      this.getNotes();
   },
   watch: {
      notes: {
         handler(updatedList) {
            localStorage.setItem("notes", JSON.stringify(updatedList));
         },
         deep: true,
      },
   },
   methods: {
      getNotes() {
         const localNotes = localStorage.getItem("notes");
         if (localNotes) {
            this.notes = JSON.parse(localNotes);
         }
      },
      handleSubmit(inputTitle, inputDescription) {
         this.notes.push({
            title: inputTitle,
            description: inputDescription,
         });
      },
   },
};
</script>

<style lang="scss" scoped>
.home-page {
   max-width: 1140px;
   margin:  0 auto;
   padding: 0 15px;
}
.title {
   font-size: 25px;
   font-weight: 600;
   margin: 0px 0px 20px 0px;
   padding: 0px 0px 0px 5px;

   @media (max-width: 700px) {
      text-align: center;
      padding: 0;
   }
}
.container {
   display: flex;
   align-items: flex-start;
   gap: 20px;

   @media (max-width: 700px) {
      flex-direction: column;
      align-items: center;
      justify-content: center;
   }
}
.empty {
   margin: 0px 0px 0px 10%;
   align-self: center;
   color: #b9b9bd;
   
   @media (max-width: 700px) {
      margin: 0 auto;
   }
}
</style>
