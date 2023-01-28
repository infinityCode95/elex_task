<template>
   <div class="noteitem-page">
      <div class="container">
         <header class="noteitem__header">
            <router-link to="/">
               <a class="noteitem__link">Главная</a>
            </router-link>
            <span> / </span>
            <span>Test</span>
         </header>

         <div class="noteitem__content">
            <h3 class="noteitem__title">{{ $route.params.title }}</h3>
            <p class="noteitem__description">{{ $route.params.description }}</p>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   name: "NoteItemView",
};
</script>

<style lang="scss" scoped>
.noteitem-page {
   max-width: 1140px;
   margin:  0 auto;
   padding: 0 15px;
}

.noteitem__header {
   margin: 0px 0px 15px 0px;

   span {
      color: #7c7c7f;
   }
}

.noteitem__link {
   color: blue;
   text-decoration: underline;
}

.noteitem__content {
}

.noteitem__title {
   margin: 0px 0px 15px 0px;
   font-size: 22px;
   font-weight: 600;
}

.noteitem__description {
   font-size: 14px;
}
</style>

