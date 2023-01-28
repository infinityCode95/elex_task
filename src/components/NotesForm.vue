<template>
   <div class="notesform">
      <div class="form__wrap">
         <form class="form" @submit.prevent="onSubmit">
            <label class="form__label" for="title">Заголовок</label>
            <input
               class="form__input form__input-title"
               type="text"
               required
               name="title"
               v-model.trim="inputTitle"
            />
            <label class="form__label" for="description">Описание</label>
            <input
               class="form__input form__input-description"
               type="text"
               required
               name="description"
               v-model.trim="inputDescription"
            />
            <button class="form__btn" type="submit">Добавить</button>
         </form>
      </div>
   </div>
</template>
  
<script>
export default {
   name: "NotesForm",
   data: () => ({
      inputTitle: "",
      inputDescription: "",
   }),

   methods: {
      onSubmit() {
         this.$emit("emitOnSubmit", this.inputTitle, this.inputDescription);
         this.inputTitle = "";
         this.inputDescription = "";
      },
   },
};
</script>
  
<style lang="scss" scoped>
.form__label {
   font-size: 14px;
}
.form__input {
   display: block;
   border: 2px solid rgb(191, 189, 189);
   outline: none;
   padding: 0px 0px 0px 7px;
   border-radius: 3px;
   margin: 5px 0px 15px 0px;
   width: 300px;   
   height: 30px;

   @media (max-width: 700px) {
      width: 70vw;
   }
}

.form__input-description {
   height: 50px;
}
.form__btn {
   padding: 7px 10px;
   background-color: blue;
   color: #fff;
   font-weight: 500;
   border-radius: 5px;

   @media (max-width: 700px) {
      width: 100%;
   }
}
</style>