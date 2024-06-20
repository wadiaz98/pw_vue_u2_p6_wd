<template>
  <div class="opciones-container">
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
    </ul>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.opciones-container {
    display: flex;
    justify-content: center;
}
ul{
    list-style-type: none;
}
li{
    border: 1px solid black;
    border-radius: 5px;
    margin-bottom: 10px;
    width: 250px;
    background: rgb(193, 193, 193);
    cursor: pointer;
}

li:hover{
    background: rgb(156, 156, 156);
    
}
</style>