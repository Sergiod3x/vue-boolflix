<template>
    <div>
        <div class="navbar">
        <div class="logo"><img src="../assets/logo.png" alt=""></div>
       <input type="text" placeholder="Search" v-model="searchString"
       @keyup.enter="$emit('search', searchString)"/>
       </div>
    </div>
</template>

<script>
export default{
   name : "Nav",
   data() {
       return{
           searchString : ""
       }

   }
}
</script>

<style lang="scss" scoped>

.navbar{
    display: flex;
    justify-content: space-between;
    .logo img{
        height: 25px;
        padding-top: 5px;
        padding-left: 5px;
    }

        
    background-color: black;
}

</style>