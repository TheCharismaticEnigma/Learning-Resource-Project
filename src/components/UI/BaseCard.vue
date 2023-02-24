<!-- Component is a UI style component responsible
for giving the card-like-style to other components. 
 -->
<!-- receives content dynamically using slots. -->

script
<script>
export default {};
</script>

<template>
  <div class="container card-wrapper">
    <slot name="cardContent"> </slot>
  </div>
</template>

<!-- Separate container from Content. 
     Separate Structure from Skin
     Just a wrapper. The alignment of items 
     is handled by individual containers. 
 -->

<!-- Margins and paddings will be added on individual 
 container elements.  -->

<style scoped>
.card-wrapper {
  border-radius: 10px;
  box-shadow: 1px 0px 8px 0 darkgray;
}
</style>
