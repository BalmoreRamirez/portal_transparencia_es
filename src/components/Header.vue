<template>
  <div class="header-title">
    <h2>{{ titulo }}</h2>

  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      titulo: "Bienvenidos al portal de transparencia",
    }
  }
}
</script>

<style scoped>
.header-title {
  width: 100%;
  height: 100px;
  background-color: #42b983;
  font-family: "Calibri Light";
  color: aliceblue;
  text-align: center;

  margin-top: 10px;

}
</style>