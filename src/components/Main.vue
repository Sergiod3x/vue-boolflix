<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="films">
                    <Film v-for="(films, index) in films" :key="index"
                    :films="films" />
                </div>
            </div>
        </div>

    </div>
    
    
</template>

<script>
import Film from "./Film.vue";
export default{
   name : "Main", 
   components: {
       Film
   },
   props : {
       films : Array
   }
}
</script>

<style lang="scss" scoped>
.films{
    display: flex;
    justify-content: center;
      flex-wrap: wrap;
}

</style>