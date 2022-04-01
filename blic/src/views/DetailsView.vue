<template>
  <div>
    <ul>
      <li>Ime autora: {{book.authors}}</li>
      <li>ISBN: {{book.isbn}}</li>
      <li>Broj Stranica: {{book.numberOfPages}}</li>
      <li>Zemlja podrjetla: {{book.country}}</li>
      <li>Izdano: {{book. released}}</li>
      <li>Likovi: {{likovi.length}}</li>
    </ul> 
     <button onclick="location.href='/'">
        Back
      </button>

  </div>
</template>

<script>
export default {
  name: 'DetailsView',
  props: {
    isbn: String,
    url: String
  },

  data(){
    return{
      book:[],
      likovi:0
    }
  },
  
  created: async function() {
    let get_request = await fetch(this.url)
    let response = await get_request.json() 
    this.book = response
    this.likovi = response.characters
  }

}
</script>