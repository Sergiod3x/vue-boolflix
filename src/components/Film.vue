<template>

    <div>
        <div class="film">
            <img src="https://image.tmdb.org/t/p/w342/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg" alt="">
            <div class="info">
                <H4>Titolo :</H4>   {{films.title}} 
                <H4>Titolo originale:   </H4>  {{films.original_title}}
                <h4>Lingua originale</h4>{{films.original_language}} 
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
}

.film:hover .info{
  display: block;
}

</style>