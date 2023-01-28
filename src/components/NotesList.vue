<template>
   <div class="notes__list">
      <div class="note__item" v-for="note in items" :key="note">
         <div class="note__item-content">
            <div class="note__item-header">
               <h3 class="note__item-title">{{ note.title }}</h3>
               <p class="note__item-description">{{ note.description }}</p>
            </div>
            <div class="note__item-btns">
               <router-link :to="{ name: 'noteitem', params: { title: note.title, description: note.description }}">
                  <button class="note__item-btn btn__open">Открыть</button>
               </router-link>
               <button @click="onRemove(note)" class="note__item-btn btn__remove">Удалить</button>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
export default {
  name: "NotesList",
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    onRemove(note) {
      const indexOfNote = this.items.indexOf(note);
      this.items.splice(indexOfNote, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
.notes__list {
   display: flex;
   gap: 15px;
   flex-wrap: wrap;
   max-width: 800px;

   @media (max-width: 700px) {
      justify-content: center;
   }
}

.note__item {
   border: 2px solid rgb(191, 189, 189);
   padding: 10px;
   border-radius: 4px;
   width: 250px;
   cursor: pointer;

   &:hover {
      box-shadow: 0px 0px 10px 0px rgba(34, 60, 80, 0.2) inset;
      transition: all 0.2s ease;
   }
}

.note__item-content {
   display: flex;
   flex-direction: column;
   min-height: 100%;
}

.note__item-header {
   flex: 1 0 auto;
}

.note__item-title {
   font-size: 18px;
   font-weight: 500;
   margin: 0px 0px 10px 0px;
}

.note__item-description {
   font-size: 14px;
   margin: 0px 0px 20px 0px;
   max-height: 70px;
   overflow-y: hidden;
}

.note__item-btns {
   display: flex;
   justify-content: space-between;
   gap: 30px;
   flex: 0 0 auto;
}

.note__item-btn {
   padding: 5px 10px;
   border-radius: 4px;
}

.btn__open {
   border: 1px solid blue;
   color: blue;

   &:hover {
      background-color: blue;
      color: #fff;
      transition: all .3s ease;
   }
}

.btn__remove {
   border: 1px solid red;
   color: red;

   &:hover {
      background-color: red;
      color: #fff;
      transition: all .3s ease;
   }
}
</style>