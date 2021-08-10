<template>

  <div >
    <h1 class="mt-4 text-center">News Data Table</h1>
   
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col" >title</th>
          <th scope="col" >author</th>
          <th scope="col" >image</th>
          <th scope="col" >description</th>
          <th scope="col" >Detail Page</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(entry , index) in info" :key="entry.id">
          <td>{{entry.title}}</td>
          <td>{{entry.author}}</td>
          <td><img class="img" :src="entry.urlToImage" /></td>
          <td>{{entry.description}}</td>
        <button  class="blueButton" @click="goToHome(`${index + 1}`, entry)">View Detail</button>
        
         </tr>
      </tbody>
    </table>
  </div>  
</template>

<script>
import axios from 'axios';

export default {
  name: "HelloWorld",
  props: ['entry.title', 'info'],
 data:()=>{
   return {
      info: null
     }
 },
 mounted () {
    axios
      .get('https://newsapi.org/v2/everything?q=tesla&from=2021-07-10&sortBy=publishedAt&apiKey=fc8c95be6c5a49d89fdcf9be04745cc2')
      .then(response => {
        console.log(response)
        console.log (response.data.articles?.filter((ele, index) => index === 8))
        return (this.info = response.data.articles)
      })

  }
,
  methods: {
     goToHome(id, entry){

       localStorage.setItem("page_index", id);
       localStorage.setItem("page_data", JSON.stringify(entry));
       this.$router.push({name: 'DetailPage', params: { id: id},}); 
      },

  },
};
</script>
<style>


table {
  font-family: 'Open Sans', sans-serif;
  width: 100%;
  border-collapse: collapse;
  border: 3px solid rgb(148, 148, 8);
  margin: 10px;
}

table th {
  text-transform: uppercase;
  text-align: center;
  background: #ffc107 !important;
  color: black;
  cursor: pointer;
  padding: 8px;
  min-width: 30px;
}
table th:hover {
  background: #717699;
  color: blanchedalmond;
}
table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
   color: black;
}

.img{
  width: 70%;
  height: 10rem;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.blueButton {
  color: rgb(217, 206, 206);
  background-color: rgb(30, 69, 212) !important ;
  border-radius: 5px;

}


</style>