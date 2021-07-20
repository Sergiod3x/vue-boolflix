<template>

    <div>
        <div class="film">
            <img :src="imgSrc(films.poster_path)" alt=""/>
            <div class="info">
                <div class="text">
                    <H4>Titolo :</H4>   {{films.title}} 
                    <H4>Titolo originale:   </H4>  {{films.original_title}}
                    <h4>Lingua originale</h4><img class="flag" :src="returnFlag(films.original_language)" alt="" />
                    <div class="vote">
                        <h4>Popolarità</h4>
                        <ul v-if="vote > 0"> 
                            <li><i class="fas fa-star gold"></i></li>
                            <li v-if="vote > 1"><i class="fas fa-star gold"></i></li>
                            <li v-else><i class="far fa-star "></i></li>
                            <li v-if="vote > 2"><i class="fas fa-star gold"></i></li>
                            <li v-else><i class="far fa-star"></i></li>
                            <li v-if="vote > 3"><i class="fas fa-star gold"></i></li>
                            <li v-else><i class="far fa-star"></i></li>
                            <li v-if="vote > 4"><i class="fas fa-star gold"></i></li>
                            <li v-else><i class="far fa-star"></i></li>
                        </ul>
                    </div>

                </div>
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
   data(){
    return{
        vote: Math.round(this.films.popularity / 2),
      languageArray:["it","de","en","es","fr","pt"],
      }
    },
    methods:{
        imgSrc(partialSrc){
            return  "https://image.tmdb.org/t/p/w342"+ partialSrc;
        },
        returnFlag(Language) {
            //Se non ho la bandiera corrispondente stampo la bandiera della terra
            if(this.languageArray.includes(Language)){
                return require("../assets/flags/" + Language + ".svg");
            }
            return require("../assets/flags/all.png");
        
    }
  }
  }

</script>

<style lang="scss" scoped>
.film{
    position: relative;
    margin:25px;
    .info{
        background-color: rgba(0, 0, 0, 0.452);
        width: 100%;
        height: 100%;
        position: absolute;
        bottom: 0px;
        color: whitesmoke;
        display: none;
        .text{
            padding : 25px;
        .flag {
            width: 25px;
            }
        .vote{
            display: flex;
            align-items: center;
            line-height: 18px;
            ul {
                display: flex;
                margin-top: 5px;
                list-style-type: none;
                align-items: center;
                
            }

        }

        }
    }

}

.film:hover .info{
  display: block;
}

.gold{
    color: gold;
}


</style>