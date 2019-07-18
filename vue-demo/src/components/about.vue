<template>
  <div class="about">
    <h1>Hallo {{ their_name }}, this is an About</h1>
    <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Magnam blanditiis dolores possimus soluta sint itaque? Incidunt recusandae aliquam architecto enim corrupti corporis doloribus, repudiandae fuga, commodi odit dolore quae necessitatibus?</p>
  <div class="card" style="width: 18rem;">
  <ul class="list-group list-group-flush">
    <li class="list-group-item">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Vestibulum at eros</li>
  </ul>
</div>
  
  
  </div>
</template>
<script>
export default {
  name: "homes",
  data() {
    return {
      their_name: this.$route.params.name
    };
  }
};
</script>