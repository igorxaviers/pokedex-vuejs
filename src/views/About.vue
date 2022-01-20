<template>
  <div class="about">
    <h1>This is an about page {{idBusca}}</h1>

  </div>
</template>
<script>
export default {
  created() {
    console.log(this.$route.params.id);
    console.log('about created');
    this.idBusca = this.$route.params.id;
  },
  data() {
    return {
      idBusca: 0
    };
  }
}
</script>
