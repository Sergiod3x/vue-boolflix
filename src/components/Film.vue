<template>

    <div>
        <div class="film">
            <img :src="imgSrc(films.poster_path)" alt=""/>
            <div class="info">
                <H4>Titolo :</H4>   {{films.title}} 
                <H4>Titolo originale:   </H4>  {{films.original_title}}
                <h4>Lingua originale</h4><img class="flag" :src="returnFlag(films.original_language)" alt="" />
                <h4>Popolarità</h4>{{films.popularity}}
            </div>
        </div>
    </div>
 
    
</template>

<script>
export default{
   name : "Album", 
   props : {
       films : Object
   },
    methods:{
        imgSrc(partialSrc){
            return  "https://image.tmdb.org/t/p/w342"+ partialSrc;
        },
        returnFlag(Language) {
        return require("../assets/flags/" + Language + ".svg");
    },
  }
}
</script>

<style lang="scss" scoped>
.info{
  width: 100%;
  position: absolute;
  bottom: 20px;
  color: whitesmoke;
  display: none;
  .flag {
      width: 25px;
    }
}

.film:hover .info{
  display: block;
}

</style>