<template>
  <div class="view" >
    <h1 class="mt-4 text-center topbar">View Detail of News created on {{page_data.publishedAt}}</h1>
    <div class="title">
     <h3 class="mt-4 text-center">{{page_data.title}}</h3>
    </div>
 
  <div class="row g-0">
    <div class="col-4">
      <img :src="page_data.urlToImage" class="img-fluid img-thumbnail image" alt='' />
    </div>
    <div class="col-8">
      <div class="author"> Author is {{page_data.author}}</div>
      <div class="des"> <strong >Description of new is</strong> <br> {{page_data.description}}</div>
    </div> 
  </div>
</div>
</template>

<script>



export default {
 
  name: "DetailPage",
    props: ['id' ],
 data:()=>{
   return {
     page_data: JSON.parse(localStorage.getItem("page_data"))
     }
 },
 mounted () {
   console.log({page: this.page_data})
 },
  methods: {
  },
};
</script>

<style>

.view{
  margin:20px
}
.topbar{
  background-color: #ffc107;
}
.title{
  display: flex;
  height: 70px;
  width: 100%;
  background-color: #916f09;
  align-items: center;
 justify-content: center;
 color:white
}

.author{
  height: 70px;
display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffc10747;
}
.des{
  background-color: rgba(128, 128, 128, 0.438);
  color: black;
  height: 300px;

}
.image{
  width: 100%;
  height: 20rem;
}
</style>