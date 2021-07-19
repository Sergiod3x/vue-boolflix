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
    searchAlbum(albumString){
      let searchBottString = "https://api.themoviedb.org/3/search/movie?api_key=e4d8fd5e18690e57267700ebfb913c8d&query="+albumString;
      axios.get(searchBottString).then((result)=> {
      this.filteredArray = result.data.results
       console.log("ciao")
         console.log("ciao")
            console.log(this.filmfilteredArray)
    })
      
      this.filteredArray = this.filmsArray.filter((element)=>{
        // console.log("stringa"+albumString);
        // console.log(element);
        // console.log("anno" +element.year);
        // console.log("return" +element.year.includes("albumString"));
        if ((element.title.toLowerCase().includes(albumString.toLowerCase()))||(element.original_title.toLowerCase().includes(albumString.toLowerCase()))){
          return true
        }
        false
      })

       

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
