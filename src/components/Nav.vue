<template>
    <div>
        <div class="navbar">
            <div class="logo"><img src="../assets/logo.png" alt=""></div>
            <div>

                <input type="text" placeholder="Search" v-model="searchString"
                @keyup.enter="$emit('search', searchString)"/>
                <button @click="$emit('search', searchString)"><i class="fas fa-search"></i></button> 
            </div>
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
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px;
    .logo img{
        height: 25px;
        margin-top: 5px;

    }
        
    background-color: black;
}

</style>