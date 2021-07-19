<template>
  <div id="app">
    <!-- <Loader v-if="(isNaN(albums.page) )"/> -->
    <!-- <button @click="searchAlbum(filteredArray)">Filtra</button> -->
    <Nav  @search="searchAlbum"/>
    <Main :films="filteredArray"/>

  </div>
</template>

<script>
import axios from "axios";
import Nav from "./components/Nav.vue";
import Main from "./components/Main.vue";
// import Loader from "./components/Loader.vue";

export default {
  name: 'App',
  components: {
    Nav,
    Main,
    // Loader,
  },
  data(){
    return{
      albums:{},
      filteredArray:[],
      filmsArray:[],

    }
  },
  created(){
    //alla creazione carico la lista di film preferiti del periodo
    axios.get("https://api.themoviedb.org/3/movie/popular?api_key=e4d8fd5e18690e57267700ebfb913c8d&language=it-US&page=1").then((result)=> {
      this.albums = result
      this.filteredArray = result.data.results
      this.filmsArray= result.data.results
       console.log("ciao")
      console.log(this.albums)
         console.log("ciao")
            console.log(this.filmsArray)
    })
  },
  methods:{
    salutami(mex){
      alert(mex); 
    },
    searchAlbum(searchString){
      if(searchString.length == 0){
        this.filteredArray=  this.filmsArray;
      } else{
        let searchBottString = "https://api.themoviedb.org/3/search/movie?api_key=e4d8fd5e18690e57267700ebfb913c8d&query="+searchString;
        axios.get(searchBottString).then((result)=> {
        this.filteredArray = result.data.results
         console.log("ciao")
           console.log("ciao")
              console.log(this.filteredArray)
      
        })
      } 

    }
  }
}
</script>

<style lang="scss">

@import "./style/app.scss";
#app{
  background-color:$primary-color ;
}
// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
