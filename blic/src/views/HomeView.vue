<template>
  <div class="home">
    <ol>
      <li v-for="book in books" :key="book.url">
        <!-- <router-link :to="'/commit_details/' + commit.sha">{{ commit.sha }}</router-link> -->
        <router-link :to="{name:'details', params: { isbn: book.isbn, url: book.url}}">{{ book.name }}</router-link>
      </li>
    </ol>
    
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name:'HomeView',
  data() {
    return {
      books: []
    }
  },

  mounted: async function() {
     let get_request = await fetch("http://ntankovic.unipu.hr:8000/api/books")
     console.log("requested")
     let response = await get_request.json() //lokalna varijabla; vidljiva samo u mounted fun
     this.books = response //this se referencira na objekta kojeg sam eksportirao (export default ili data?)
  }

}
</script>