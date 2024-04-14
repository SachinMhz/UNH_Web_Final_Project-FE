<template>
    

    <div  :class="book.published ? 'green': 'red' ">

                        <h2>{{book.title}}</h2>
                        <h4> {{book.year}}</h4>
                        <h4> {{book.published}}</h4>
    </div>
</template>

<script>

export default{
    name: 'SingleBook',
    props:{
        book: Array
    }
}
</script>

<style scoped>

.green{
    background-color: green;
}

h4{
    margin: 2px;
}

div{
    background-color: #ffb89e;
    color: black;
    padding: 1em;
    text-align: center;
    width: 80%;
    margin: auto;
    

}

.red{
background-color: orangered !important;

}


</style>