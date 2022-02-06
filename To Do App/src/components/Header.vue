<template>
  <header>
    <div class="header_content">
      <h1>{{ title }}</h1>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      title: "To Do App",
    };
  },
};
</script>
<style scoped>
header {
  border-bottom: 1px solid #303030;
  width: 100%;
}
.header_content {
  max-width: 1024px;
  margin: 0 auto;
}
h1 {
  color: red;
  text-align: left;
  margin: 15px 0 5px 10px;
}
</style>