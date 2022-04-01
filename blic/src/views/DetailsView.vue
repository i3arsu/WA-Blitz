<template>
  <div>
    <h1>{{book.name}}</h1>
    <ul>
      <li>Ime autora: {{book.authors}}</li>
      <li>Broj Stranica: {{book.book.numberOfPages}}</li>
      <li>Zemlja podrjetla: {{book.book.country}}</li>
      <li>Izdano: {{book.book.released}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'DetailsView',
  props: {
    isbn: String
  },

  data(){
    return{
      book:[]
    }
  },
  
  created: async function() {
    
    let get_request = await fetch("https://www.anapioficeandfire.com/api/books")
    let response = await get_request.json() 
    this.book = response
  }

}
</script>