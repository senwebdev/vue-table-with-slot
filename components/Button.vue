<template>
   <button class="btn" :class="`btn-${type}`">
      <slot></slot>  
   </button>
</template>

<script>
export default {
 props: {
   type:{
     type: String
   }
 }
}
</script>

<style lang="scss">
$primary-color: #66615B;
$danger-color: #EB5E28;
.btn{
  border: 2px solid $primary-color;
  padding: 10px;
  font-size: 16px;
  border-radius: 20px;
  color: $primary-color;
  &.btn-danger{
    color: $danger-color;
    border-color: $danger-color;
    &:hover{
     background-color:$danger-color;
     color: white;
    }
  }
  &:hover {
    background-color:$primary-color;
    color: white;
    cursor:pointer;
  }
}

</style>
