<template>
    <div>
        <div class="films">
        <Film v-for="(films, index) in films" :key="index"
         :films="films" />
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
    justify-content: space-between;
}

</style>